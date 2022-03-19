# Database-HW8 Answer for Question 5
### create database
```py
use User
```
<img width="151" alt="image" src="https://user-images.githubusercontent.com/69972884/159114031-6466ea65-ef71-4834-87d0-22a49c0df132.png">

### create Students table
```py
db.createCollection("Students")
```
<img width="207" alt="image" src="https://user-images.githubusercontent.com/69972884/159114086-f23f41b0-9c51-4ee9-b727-c5bc6ac124dd.png">

### insert students data
```py
db.Students.insertMany(
    [
        {"name":"Ramesh","subject":"maths","marks":87},
        {"name":"Ramesh","subject":"english","marks":59},
        {"name":"Ramesh","subject":"science","marks":77},
        {"name":"Rav","subject":"maths","marks":62},
        {"name":"Rav","subject":"english","marks":83},
        {"name":"Rav","subject":"science","marks":71},
        {"name":"Alison","subject":"maths","marks":84},
        {"name":"Alison","subject":"english","marks":82},
        {"name":"Alison","subject":"science","marks":86},
        {"name":"Steve","subject":"maths","marks":81},
        {"name":"Steve","subject":"english","marks":89},
        {"name":"Steve","subject":"science","marks":77},
        {"name":"Jan","subject":"english","marks":0,"reason":"absent"}
    ]
)
```
<img width="518" alt="image" src="https://user-images.githubusercontent.com/69972884/159114185-76e32058-6299-41fc-bb1c-0ab72433a1c1.png">

### Find the total marks for each student across all subjects.
```py
db.Students.aggregate([{$group:{_id:"$name",total_mark:{$sum:"$marks"}}}])
```
<img width="447" alt="image" src="https://user-images.githubusercontent.com/69972884/159114212-c7e6d046-8a15-49f1-b137-036317412341.png">

### Find the maximum marks scored in each subject. 
```py
db.Students.aggregate([{$group:{_id:"$subject",max:{$max:"$marks"}}}])
```
<img width="442" alt="image" src="https://user-images.githubusercontent.com/69972884/159114268-f394f19d-8821-4011-a70f-6684954ceefa.png">

### Find the minimum marks scored by each student. 
```py
db.Students.aggregate([{$group:{_id:"$subject",min:{$min:"$marks"}}}])
```
<img width="441" alt="image" src="https://user-images.githubusercontent.com/69972884/159114283-1f11936c-37bc-4169-95ca-8d5f145460db.png">

### Find the top two subjects based on average marks.
```py
db.Students.aggregate([{$group:{_id:"$subject",avg:{$avg:"$marks"}}}, {$sort:{"avg":-1}}, {$limit: 2}])
```
<img width="654" alt="image" src="https://user-images.githubusercontent.com/69972884/159114311-650cdc4e-bc82-46c1-aefc-e840e9101c5d.png">

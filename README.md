# SQL-PROJECT
# ATTENDANCE MONITORING SYSTEM
CREATE TABLE Attendancee (
  staff_id varchar(50),
  batch_id Int primary key  ,
  students_id varchar(50),
  students_name varchar(50)
  );


  CREATE TABLE Batch (
  batch_id Int,
  subject_ varchar(50),
  day_ varchar(50),
  hour_ varchar(50),
  foreign key (batch_id) references attendancee (batch_id)
  );



 CREATE TABLE Faculties (
  faculty_id int primary key ,
  first_name varchar(50),
  last_name varchar(50),
  salary varchar(50)
  );


CREATE TABLE Students (
  student_id int ,
  st_name varchar(50),
  gender varchar(50),
  section varchar(50),
  faculty_id int ,
  foreign key (faculty_id) references faculties (faculty_id)  
  );


insert into attendancee (staff_id,batch_id,students_id,students_name) values
(01,101,21,"varun"),
(02,102,22,"mithun"),
(03,103,23,"arun"),
(04,104,24,"tharun"),
(05,105,25,'Suresh'),
(06,106,26,'Ramesh'),
(07,107,27,'Ganesh'),
(08,108,28,'Dinesh'),
(09,109,29,'Rakesh'),
(10,110,30,'Mahesh');


insert into batch (batch_id,subject_,day_,hour_) values
(101,"tamil","monday","1hour"),
(102,"english","friday","2hour"),
(103,"maths","thursday","3hour"),
(104,"science","wednesday","4hour"),
(105,'history','tuesday','1hour'),
(106,'geography','monday','2hour'),
(107,'physics','friday','3hour'),
(108,'chemistry','thursday','4hour'),
(109,'biology','wednesday','2hour'),
(110,'computer science','tuesday','3hour');

insert into Faculties (faculty_id,first_name,last_name,salary) values
(301,"siva","kumar",20000),
(302,"muthu","arasan",25000),
(303,"deepak","dharsan",30000),
(304,"sibi","raj",35000),
(305,'naveen','kumar',28000),
(306,'priya','venkat',32000),
(307,'ravi','shankar',27000),
(308,'meena','krishnan',33000),
(309,'ganesh','babu',29000),
(310,'swetha','ram',31000);


insert into Students (student_id,first_name,gender,section,faculty_id) values
(111,"arsath","male","A",301),
(112,"abinas","male","B",302),
(113,"vignesh","male","A",303),
(114,"valli","female","B",304),
(115,'priya','female','A',305),
(116,'karthik','male','B',306),
(117,'sneha','female','A',307),
(118,'arjun','male','B',308),
(119,'divya','female','A',309),
(120,'rajesh','male','B',310);



# 1. Retrieve all records where the students_name starts with 'R'.


     SELECT * FROM Attendancee WHERE students_name LIKE 'R%';


# 2. Find the students_name and batch_id of students whose batch_id is greater than 105.


     SELECT students_name, batch_id FROM Attendancee WHERE batch_id > 105;

# 3. Retrieve the total number of students in the Attendancee table.


     SELECT COUNT(*) AS total_students FROM Attendancee;

# 4.  List all records sorted by students_name in ascending order.


     SELECT * FROM Attendancee ORDER BY students_name ASC;


 # 5. Add a new column named classroom to the Batch table.

     ALTER TABLE Batch ADD COLUMN classroom VARCHAR(50);


# 6. Group the records by day_ and count the number of batches scheduled for each day.

     SELECT day_, COUNT(*) AS total_batches FROM Batch GROUP BY day_;



# 7.  Count the number of faculty members with a salary between 25000 and 30000.

      SELECT COUNT(*) AS num_faculties FROM Faculties WHERE salary BETWEEN 25000 AND 30000;


# 8. Find the faculty member with the highest salary.


       SELECT * FROM Faculties ORDER BY salary DESC LIMIT 1;


# 9. List the first and last names of faculty members whose last name is 'kumar'.

     SELECT first_name, last_name FROM Faculties WHERE last_name = 'kumar';


# 10. The column hour_ has been renamed to duration.

     ALTER TABLE Batch DROP COLUMN day_;


# 11. What are the Details of Attendancee and Batch table.

    select  * from attendancee JOIN  batch ON attendancee.batch_id =batch.batch_id;


# 12.List the first_name,salary,gender Left join faculties and students.

   select first_name,salary,gender from faculties left join students ON faculties.faculty_id=students.faculty_id;


# 13. Retrieve st_name,gender,section,faculty_id from students.

   Create view sqlproject AS select st_name,gender,section,faculty_id from students;

# 14.Create stored procedure from Batch Table.


   DELIMITER $$
create procedure getfaculty()
BEGIN
select * from batch;
END $$
DELIMITER ;

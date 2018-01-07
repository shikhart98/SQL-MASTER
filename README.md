# SQL-MASTER


SOME BASIC DEFINATIONS 

# primary key:
is the one which defines some basic definitions in the table uniquely.
hence for the purpose of assigning IDs and all , we use primary keys. 
syntax :: id INETEGER PRIMARY KEY

# a "group by" claus 
is necessary before "having" statement.

SEE OUTPUTS HERE: https://www.khanacademy.org/computer-programming/new/sql

--------------------------------------------------------
CREATE TABLE groceries (id INTEGER PRIMARY KEY, name TEXT , quantity INTEGER,aisle INTEGER);



INSERT INTO groceries VALUES(1,"banana",13,7);

INSERT INTO groceries VALUES(12,"apples",23,6);

INSERT INTO groceries VALUES(3,"oranges",33,3);

INSERT INTO groceries VALUES(4,"kiwi",43,12);

INSERT INTO groceries VALUES(5,"guava",53,7);

INSERT INTO groceries VALUES(0,"mango",63,6);

INSERT INTO groceries VALUES(7,"pineapples",73,12);

INSERT INTO groceries VALUES(18,"watermelon",83,3);

INSERT INTO groceries VALUES(19,"cherry",83,3);

INSERT INTO groceries VALUES(10,"grapes",93,12);



SELECT * FROM groceries WHERE id > 11;



SELECT SUM(quantity) FROM groceries WHERE id>11;



SELECT MAX(id) FROM groceries;



SELECT * FROM groceries;



SELECT aisle,SUM(quantity) FROM groceries GROUP BY aisle;

----------------------------'''''-----------------------------


CREATE TABLE exercise(id INTEGER PRIMARY KEY AUTOINCREMENT,
type TEXT,
minutes INTEGER,
calories INTEGER,
heart_rate INTEGER);



INSERT INTO exercise (type,minutes,calories,heart_rate) VALUES ("biking",20,300,79);


INSERT INTO exercise (type,minutes,calories,heart_rate) VALUES ("running",120,320,90);


INSERT INTO exercise (type,minutes,calories,heart_rate) VALUES ("running",10,30,90);


INSERT INTO exercise (type,minutes,calories,heart_rate) VALUES ("cycling",30,200,92);



SELECT * FROM exercise;



SELECT * FROM exercise WHERE calories>290 ORDER BY calories DESC;



-- AND operator


SELECT * FROM exercise WHERE calories > 290 AND minutes < 100 ;



-- OR operator


SELECT * FROM exercise WHERE calories >200 OR
 minutes>50;


SELECT * FROM exercise WHERE type = "running";



--  IN operator 
 

SELECT * FROM exercise WHERE type IN("running" , "biking");


--NOT IN operator
SELECT * FROM exercise WHERE type NOT IN("running" , "biking");




CREATE TABLE doctor (id INTEGER PRIMARY KEY , 
type TEXT,
reason TEXT);



INSERT INTO doctor(type,reason) VALUES ("biking","improves cardiovascular flow in body");


INSERT INTO doctor(type,reason) VALUES ("cycling","improves muscular readjustment");



SELECT * FROM doctor;



--LIKE OPERATOR
SELECT * from exercise WHERE type IN (SELECT type FROM doctor WHERE reason LIKE "%cardiovascular%");



SELECT type,SUM(calories) FROM exercise GROUP BY type;


-- AS function


SELECT type, SUM(calories) AS total_calories FROM exercise GROUP BY type;


SELECT type, SUM(calories) AS total_calories FROM exercise GROUP BY type HAVING total_calories >200 ;



-- avg function


SELECT type, AVG(calories) AS avg_calories FROM exercise GROUP BY type ;



-- count operator


SELECT * FROM exercise GROUP BY type HAVING COUNT(*) >1;


-- ROUND and using +,-,*,/ operators


SELECT COUNT(*) FROM exercise WHERE
 heart_rate >= ROUND(0.50*(210-30));


--UPDATE
UPDATE exercise SET minutes = 40,calories =120 WHERE type = "biking";


select * from exercise;



--DELETE
DELETE FROM exercise WHERE id =2;


select * from exercise;

-- ALTER TABLE


alter table exercise ADD sets INTEGER default 0;


select * from exercise;



INSERT INTO exercise (type,minutes,calories,heart_rate,sets) VALUES ("jumping",20,100,99,5);


select* from exercise;



UPDATE exercise SET sets = 20 where type = "biking";


SELECT* FROM exercise;


-- DROP TABLE 

DROP TABLE exercise;
 //this deletes the table from the database;

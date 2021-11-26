# SQL
SQL stands for Sequential Query Language. SQL is a language to access and manupilate databases. RDBMS is the reason why SQL exists. RDBMS stands for Relational Database System. In RDBMS data are stored in Tables.

## SQL Commands
SQL commands are instrunctions used for communicating with database. It can perform various tasks like creating table, add or update data on table, drop table etc.

__There are five types of SQL commands:__
![Types](https://static.javatpoint.com/dbms/images/dbms-sql-command.png)

1. ### DDL(Data Definition Language)
    DDL changes the structure of table like creating, deleting the table etc. These commands are auto commited.  
- __CREATE:__ It is used to create a new table in database.  
__Syntax:__
```
CREATE TABLE table_name (column_name datatypes);
```
- __DROP:__ It is used to delete the table including its data.
__Syntax:__
```
DROP TABLE Table_name;
```

- __ALTER:__ It is used to change the characteristics of existing table.
__Syntax:__  
To add a column in table
```
ALTER TABLE Table_name ADD column_name column-definition;
```
To modify the existing column in table:
```
ALTER TABLE Table_name MODIFY(column_definition);
```

- __TRUNCATE:__ It is used to delete all the data from the table but not the table itself.  
__SYNTAX:__  
```
TRUNCATE TABLE Table_name;
```

2. ### DML (Data Manipulation Language)
DML commands are used to modify the database. DML commands is not auto-committed that means it cant permanantly save all the changes in the database.

- __INSERT:__ It is used to insert data into the row.  
__SYNTAX:__
```
INSERT INTO Table_name (col1, col2, col3,...coln)
VALUES(value1, value2, value3, valuen);
```
- __UPDATE:__ It is used to update or modify value of a table.  
__SYNTAX:__
```
UPDATE Table_name SET [Column_name=value...]
WHERE condition;
```

- __DELETE:__ It is used to remove one or more row from table.
__SYNTAX:__
```
DELETE FROM Table_name  WHERE condition;
```

3. ### DCL (Data Control Language)
DCL commands are used to change the permission of a database.
- __GRANT:__ It is used to user access to a database.  
  __SYNTAX:__
```
GRANT SELECT,UPDATE ON Table_name TO User_name1, User_name2;
```
- __REVOKE:__ It is used to take back the permission from the user.
  __SYNTAX:__
```
REVOKE SELECT, UPDATE ON Table_name TO User_name1, User_name2;
```
4. ### TCL (Transaction Control Language)
   TCL commands can only be used with DML commands, since they dont support auto commit.
  - __COMMIT:__ It is used to save all the transactions to the database.  
  __SYNTAX:__
  ```
    COMMIT;
  ``` 
  - __ROLLBACK:__ It is used to undo transactions that have not been already been saved to the database.  
  __SYNTAX:__
  ```
    ROLLBACK;
  ```
  - __SAVEPOINT:__ It is used to roll the transaction back to certain point without rolling back the entire transaction.  
  __SYNTAX:__
  ```
  SAVEPOINT Savepoint_Name;
  ```
5. ### DQL (Data Query Language)
   DQL commands is used to fetch data from database.
  - __SELECT:__ It is used to select attribute based on described by where clause.  
  __SYNTAX:__
  ```
    SELECT expressions
    FROM Table_name
    WHERE condition;
  ```


## KEYS
Keys are used to uniquely define any record or row of data from the table. It is also used to identify relationships of table.

__Types of Keys:__
1. Primay Key: It is a key which uniquely define all the other attributes.  
   Example: In student table, Roll Number can be a primary key since it is unique for each student.
2. Candidate Key: It is an attribute which or group of attributes which can uniquely identify a tuple.  
   Example: In Student table, Roll number is best suited for primary key. Rest of the attributes, like address, phone number are considered as a cadidate key.
3. Super Key: Its a key which uniquely identify a tuple.  
Example: Roll number and Student name is a key. Two students can have a same name, but their roll number cannot be the same. Hence Roll number, (Roll Number, Name), etc is a superkey.
4. Foreign Key: It is a column of a table which is used to point the primary key of other table.  
Example: In college every student belongs to different departments. So we cant store information of department in student table. Hence we link them with primary key of one table.


## Normalization
Normalization is the process of removing redundancy from a relation or set of relations. Redundancy causes anamolies. Normal forms help us to reduce or eliminate redundancy.
### First Normal Form
- It state that every attribute in a relation should be single valued.

### Second Normal Form
- A relation must be in first normal form.
- There should be no partial dependency i.e., no non-prime attribute is dependent on any proper subset of any candidate key of the table.
### Third Normal Form
- Should be in second normal form.
- There should be no transitive dependency for non-prime attributes.
### BCNF (Boyce-Codd Normal Form)
- Should be in third normal form.
- For every functional dependency LHS is super key.

## Joins
In SQL join statement is used to combine data from two or more table based on common field between them.  
__Types of joins:__
- Inner Join: It selects rows from both tables as long as condition satisfies.
  ![Inner Join](https://blog.codinghorror.com/content/images/uploads/2007/10/6a0120a85dcdae970b012877702708970c-pi.png)
- Left Join: This join returns all the rows of the table on the left side of the join and matching rows for the table on right side of join. The rows with no matching side will contain null.
  ![Left Join](https://i.stack.imgur.com/VkAT5.png)
- Right Join: This join returns all rows on right side of the join and matching rows for the table on left side of join. The rows with no matching side will contain null.
  ![Right Join](http://www.databasejournal.com/img/jk_JustSQL4_image004.jpg)
- Full Join: This join combine result of both left and right join. It contains all the rows from both tables. The rows with no matching, will contain null.
  ![Full Join](https://i.stack.imgur.com/3Ll1h.png)
## Aggregate Function in SQL
In SQL aggregate is used for collecting a set of values to return a single valure.  
Here are some of the commonly used aggregate functions:
- Count(): Returns Total Number of record.
- Sum(): Returns Sum of all value particular column.
- Avg(): Returns average of particular column
- Min(): Returns minimum value of particular column.
- Max(): Returns maximum value of paricular column.  
| Id | Name | Salary |
| -- | ---- | ------ |
| 1  |  A   |   80   |
| 2  |  B   |   40   |
| 3  |  C   |   60   |
| 4  |  D   |   70   |
| 5  |  E   |   60   |
| 6  |  F   |  Null  |

count(*): 6
sum(salary): 310
avg(salary): 62
min(salary): 40
max(salary): 80

## Transactions
Transaction group set of tasts into a single unit. Each transaction begins with a specific task and ends when all the tasks in the group successfully complete. Let's take an example of a simple transaction. Suppose a bank transfers Rs 500 from A's account ot B's. This simple small transaction involve several low-level tasks.

__A Account__
Open_Account(A)
Old_Balance = A.balance
New_Balance = Old_Balance - 500
A.balance = New_Balance
Close_Account(A)
__B Account__
Open_Account(B)
Old_Balance = B.balance
New_Balance = Old_Balance + 500
B.balance = New_Balance
Close_Account(B)


## ACID Properties
ACID stands for Atomicity, Consistency, Isolation, Durability. To maintain a consistency in database, these properties are followed.

- __Atomicity__: It states that a transaction must be treated as an atomic unit, i.e. either all of its operations are executed or none. There must be no state in a database where a transaction is left partially completed.
- __Consistency__: The database must remain in consistent state after any transaction. No transaction should have any adverse effect on the data residing in the database.
- __Durability__: The database should be durable enough to hold all the altest updates even if the system fails or restart.
- __Isolation__: In database where more than one transaction are being executed simultaneously and in parallel, the property of isolation states that all the transaction will be carried out and executed as if it is the only transaction in the system.
  
## Serializability

## Indexes
Indexes are special lookup tables that the database search engine can use to speed up data retrieval. Simply put, an index is a pointer to data in a table. An index in a database is very similar to an index in the back of a book.  
__SYNTAX:__  
- Creating Index
```
CREATE INDEX index_name ON table_name;
```
- Dropping Index
```
DROP INDEX index_name;
```

## Triggers
A trigger is a stored procedure in database which automatically invokes whenever a special event in the database occurs. For example, a trigger can be invoked when a row is inserted into a specified table or when certain table columns are being updated.  
__SYNTAX__:
```
CREATE TRIGGER trigger_name
[before | after]
[DML operations(INSERT|UPDATE|DELETE)]
on table_name
[for each row]
[trigger_body]
```
Explanation:
1. Creating trigger with trigger name.
2. befor/after specifies when the trigger will be executed.
3. DML operations.
4. on table_name specifies which table trigger is associated to.
5. [for each row] specifies a row-level trigger, i.e. the trigger will be executed for each row being affected.
6. This provides the operation to be performed as trigger is fired.


## Database Isolation level
Isolatin determines how transaction integrity is visible to others, which means a transaction should take place in system in such a way that it is the only transaction that is accessing the resources in a database system. Isolation levels define the degree to which a transaction must be isolated from the data modifications made by any other transaction in the database system. A transaction isolation level is defined by the following phenomena:
- Dirty read:  A Dirty read is the situation when a transaction reads a data that has not yet been committed.
- Non Repeatable read – Non Repeatable read occurs when a transaction reads same row twice, and get a different value each time.
- Phantom Read – Phantom Read occurs when two same queries are executed, but the rows retrieved by the two, are different.  

Based on these phenomenons SQL defines four isolation levels:
1. __Read Uncommitted__:Read Uncommitted is the lowest isolation level. In this level, one transaction may read not yet committed changes made by other transaction, thereby allowing dirty reads. In this level, transactions are not isolated from each other.
2. __Read Committed__: It does not allow dirty read.The transaction holds a read or write lock on the current row, and thus prevent other transactions from reading, updating or deleting it.
3. __Repeatable Read__: In thos the transaction holds read locks on all rows it references and writes locks on all rows it inserts, updates, or deletes.
4. __Serializable__:This is the Highest isolation level. A serializable execution is guaranteed to be serializable. Serializable execution is defined to be an execution of operations in which concurrently executing transactions appears to be serially executing.

## Locking Mechanism
SQL Server locking is the essential part of the isolation requirement and it serves to lock the objects affected by a transaction. While objects are locked, SQL Server will prevent other transactions from making any change of data stored in objects affected by the imposed lock.
__Lock Modes__  
- Exclusive Lock(X): This lock type when imposed will ensure that a page or row will be reserved exclusively for the transaction that imposed the exclusive lock, as long as the transaction holds the lock.  

- Shared Lock(S): This lock type, when imposed will reserve a page or row to be available only for reading which means that any other trabsaction will be prevented to modify the locked records as long as the lock is active. However, a shared lock can be imposed by several transactions at the same time over the same page or row.

- Update Lock(U): This lock is similar to exclusive lock but is more flexible. An update lock can be imposed on a record that already has a shared lock. In such a case, the update lock will impose another shared lock on the target row. Once the transaction that holds the update lock is ready to change the data, the update lock (U) will be transformed to an exclusive lock (X).

- Intent locks(I): This lock is uded by transaction to inform another transaction about intention to acquire a lock. The purpose of such lock is to ensure data modification to be executed properly by preventing another transaction to acquire a lock on the next in hierarchy object.

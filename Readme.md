
# Library-Management-System

This repo consists of files and report of OOP Project of Group No. 54.

## Installation
* Before running the java files, ensure that jdbc is installed in your system. Below is a tutorial on how to install java.sql for MacOS usind Intellij ide.
    * [JDBC Installation](https://www.youtube.com/watch?v=avth9uyp4LE&t=236s&ab_channel=Yash)
* Now initalize a mySql database 'LIBRARY' and the required tables using the below codes
    ```sql
    CREATE IF NOT EXISTS DATABASE LIBRARY;
    USE LIBRARY;

    CREATE IF NOT EXISTS TABLE User(
    first_name VARCHAR(40) NOT NULL,
    last_name VARCHAR(40) NOT NULL,
    student_id INT NOT NULL,
    email VARCHAR(50) NOT NULL,
    password VARCHAR(30) NOT NULL,
    date_created TIMESTAMP DEFAULT NOW(),
    is_Admin BOOLEAN,
    num_borrowed INT,
    dues INT,
    login_Status BOOLEAN,
    PRIMARY KEY(student_id)
    );

    CREATE IF NOT EXISTS TABLE Library(
    book_id INT NOT NULL,
    book_name VARCHAR(20) NOT NULL, 
    book_author VARCHAR(20) NOT NULL, 
    book_available BOOLEAN NOT NULL, 
    issued_date TIMESTAMP, 
    student_id INT,
    PRIMARY KEY(book_id),
    FOREIGN KEY (student_id) REFERENCES User(student_id)
    );
    ```
* Change the username and password present in getConnection method of javaMySqlConnector.java file as shown below 
```java
 public static Connection getConnection() throws Exception{
  try{
   String driver = "com.mysql.cj.jdbc.Driver"; 
   String url = "jdbc:mysql://localhost/Library";
   String username = "username goes here";
   String password;
   {
       password = "password goes here";
   };
   Class.forName(driver);
   .
   .
   .
```
* To run the file, run the main method of LibraryManagement.java file. 
* Note - To examine the multithreading capabalities of this file, call AdminQuery/UserQuery class with parameter as explained in comments of these classes.
## Demo
Below link showcases the uses and functionality of the created app, testcases and multithreading capabalities.

[Video Drive Link](https://drive.google.com/drive/folders/1Hyknn1G2pYgW1Mmq1-5jCWI4wYNS2ZrY?usp=sharing)

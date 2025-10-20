REPORT
# Student Management System

This project is created to manage the student information 
# 📘 Objective
To design and create a simple database schema for managing students, departments, courses, and enrollments.


# Database Used
Database Name:Student Management system
# Tables
1. Department  
2. Student  
3. Course  
4. Faculty  
5. Enrollment  

 Relationships
- One Department → Many Students  
- One Department → Many Courses  
- One Department → Many Faculties  
- One Student → Many Enrollments  
- One Course → Many Enrollments  

## 🗄️ Files in this Repository
- `student_management system.sql` → SQL script to create all tables  
- `ER_diagram.png` → ER Diagram image of the database  
- `README.md` → Project details and description  

## ⚙️ Tools Used
- MySQL Workbench  
- Draw.io (for ER diagram)  

## 🧠 Key Concepts
- DDL (CREATE, ALTER, DROP)  
- Primary and Foreign Keys  
- Normalization  
- ER Diagram Design 
-- Create Database
CREATE DATABASE StudentManagementsystem;
USE StudentManagementsystem;

CODE:-<img width="1536" height="1024" alt="ChatGPT Image Oct 20, 2025, 08_35_53 PM" src="https://github.com/user-attachments/assets/c64293f1-48ed-434a-82d4-cca6ed4c77cd" />

-- Department Table
CREATE TABLE Department (
    dept_id INT AUTO_INCREMENT PRIMARY KEY,
    dept_name VARCHAR(100) NOT NULL UNIQUE
);

-- Student Table
CREATE TABLE Student (
    student_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50),
    email VARCHAR(100) UNIQUE,
    phone VARCHAR(15),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
);

-- Course Table
CREATE TABLE Course (
    course_id INT AUTO_INCREMENT PRIMARY KEY,
    course_name VARCHAR(100) NOT NULL,
    credits INT CHECK (credits > 0),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
);

-- Faculty Table
CREATE TABLE Faculty (
    faculty_id INT AUTO_INCREMENT PRIMARY KEY,
    faculty_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
);

-- Enrollment Table
CREATE TABLE Enrollment (
    enroll_id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT,
    course_id INT,
    enrollment_date DATE DEFAULT (CURRENT_DATE),
    FOREIGN KEY (student_id) REFERENCES Student(student_id),
    FOREIGN KEY (course_id) REFERENCES Course(course_id)
);




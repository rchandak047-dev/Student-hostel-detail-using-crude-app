# Student-hostel-detail-using-crude-app# Student Hostel CRUD Web Application

A simple and responsive web application for managing student records in a hostel. This project demonstrates a full CRUD (Create, Read, Update, Delete) operation using Python Flask, MySQL, and Bootstrap 5 with a dark theme.

## Features

-   **Add Student:** Add a new student with their details and assign them to a room.
-   **View Students:** Display a list of all students in a clean, tabular format.
-   **Update Student:** Edit the information of an existing student.
-   **Delete Student:** Remove a student's record from the system.
-   **Room Management:** Students can be assigned to existing rooms.
-   **Responsive Design:** The UI is built with Bootstrap 5 and is fully responsive.
-   **Dark Theme:** A modern dark theme for a comfortable viewing experience.

## Tech Stack

-   **Backend:** Python 3, Flask
-   **Database:** MySQL
-   **ORM:** SQLAlchemy
-   **Frontend:** HTML5, Bootstrap 5 (Dark Theme)
-   **Database Connector:** PyMySQL

## Prerequisites

Before you begin, ensure you have the following installed:

-   Python 3.6+
-   MySQL Server
-   pip (Python package installer)

## Installation and Setup

Follow these steps to get the application running on your local machine.

### 1. Clone the Repository

```bash
git clone <your-repo-link>
cd flask-hostel-crud
```

### 2. Set Up a Virtual Environment

It is highly recommended to use a virtual environment to manage project dependencies.

```bash
# For Windows
python -m venv venv
venv\Scripts\activate

# For macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

Install all the required Python packages from `requirements.txt` (if you have one) or manually:

```bash
pip install Flask Flask-SQLAlchemy PyMySQL
```

### 4. Database Setup

1.  Start your MySQL server.
2.  Log in to your MySQL client.
3.  Run the following SQL commands to create the database and tables. You can find the script in the project documentation or create it manually.

```sql
CREATE DATABASE hostel_db;
USE hostel_db;

CREATE TABLE rooms (
    id INT AUTO_INCREMENT PRIMARY KEY,
    room_number VARCHAR(10) NOT NULL UNIQUE,
    capacity INT NOT NULL
);

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    phone VARCHAR(20) NOT NULL,
    room_id INT,
    FOREIGN KEY (room_id) REFERENCES rooms(id) ON DELETE SET NULL
);

INSERT INTO rooms (room_number, capacity) VALUES
('A101', 2),
('A102', 2),
('B201', 3),
('B202', 3);
```

### 5. Configure Database Connection

Open the `app.py` file and update the `SQLALCHEMY_DATABASE_URI` variable with your MySQL username and password.

```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+pymysql://<your_username>:<your_password>@localhost/hostel_db'
```

### 6. Run the Application

With your virtual environment activated, run the Flask application:

```bash
python app.py
```

The application will be available at `http://127.0.0.1:5000` in your web browser.

## Usage

-   **Homepage:** View all students.
-   **Add Student:** Click the "Add New Student" button on the homepage to navigate to the creation form.
-   **Edit Student:** Click the "Edit" button next to a student's record to update their information.
-   **Delete Student:** Click the "Delete" button to remove a student. You will be asked for confirmation.

## Project Structure

```
flask-hostel-crud/
├── venv/                 # Virtual environment folder
├── static/               # Static files like CSS, JS (if any)
├── templates/            # HTML templates
│   ├── base.html         # Master template
│   ├── index.html        # Homepage (list of students)
│   ├── add_student.html  # Form to add a new student
│   └── update_student.html # Form to update a student
├── app.py                # Main Flask application file
└── README.md             # This file
```

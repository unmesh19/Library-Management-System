# Library Management System

## Overview
This Library Management System is designed to manage books and members in a library setting. It allows members to borrow books, tracks borrowed books, and enforces borrowing limits based on membership type (Student or Faculty).

## Features
- **LibraryCard**: Represents a library card with a unique ID and issue date.
- **Book**: Represents a book with a title, author, ISBN, and availability status.
- **LibraryMember**: An abstract class representing common functionality for library members.
  - **StudentMember**: Inherits from LibraryMember with a borrowing limit of 2 books.
  - **FacultyMember**: Inherits from LibraryMember with a borrowing limit of 5 books.
- **Library**: Manages a collection of books and allows for searching books based on title, author, or ISBN.

## Installation
To run this project, ensure you have Python installed. You can simply copy the code into a Python environment or IDE.

## Usage
1. **Add Books**: Books are initialized and stored in the library's collection.
2. **Create Members**: Student and Faculty members are created with unique member IDs.
3. **Borrow Books**: Members can borrow books up to their borrowing limit. The due date for borrowed books is set to 14 days from the borrowing date.
4. **Display Information**: Member details and their borrowed books can be displayed.

## Code Structure
- **LibraryCard Class**: Handles card ID and issue date.
- **Book Class**: Contains attributes for book title, author, ISBN, and methods for borrowing and returning.
- **LibraryMember Class**: Abstract class with methods for borrowing books and displaying member information.
- **StudentMember and FacultyMember Classes**: Implement member-specific functionalities and borrowing limits.
- **Library Class**: Maintains a collection of books and allows book searches.
- **Borrowing Functionality**: Randomly borrows available books for each member and displays the borrowed books.

## Sample Code Snippet
```python
# Example of creating members and borrowing books
library = Library()
students = [StudentMember(name, f"S{i+1:03d}", student_classes[i // 10]) for i, name in enumerate(student_names)]
faculty_members = [FacultyMember(name, f"F{i+1:03d}", departments[i % len(departments)]) for i, name in enumerate(faculty_names)]

all_members = students + faculty_members
random.shuffle(all_members)

borrow_books_for_all_members(all_members)

for member in all_members:
    print(f"\n{member.display_info()}")
    for book, due_date in member.borrowed_books:
        print(f"  Borrowed '{book.title}' by {book.author}, Due on: {due_date}")

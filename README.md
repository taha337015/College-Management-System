#include <iostream>
#include <vector>
#include <string>
using namespace std;

class Person {
protected:
    string name;
    int age;
public:
    Person(string name, int age) : name(name), age(age) {}
    virtual void displayInfo() = 0;
};

class Student : public Person {
private:
    string studentID;
    string course;
public:
    Student(string name, int age, string studentID, string course)
        : Person(name, age), studentID(studentID), course(course) {}

    void displayInfo() override {
        cout << "Student Name: " << name << "\nAge: " << age 
             << "\nStudent ID: " << studentID << "\nCourse: " << course << endl;
    }
};

class Staff : public Person {
private:
    string staffID;
    string department;
public:
    Staff(string name, int age, string staffID, string department)
        : Person(name, age), staffID(staffID), department(department) {}

    void displayInfo() override {
        cout << "Staff Name: " << name << "\nAge: " << age 
             << "\nStaff ID: " << staffID << "\nDepartment: " << department << endl;
    }
};

class Course {
private:
    string courseName;
    string courseCode;
public:
    Course(string courseName, string courseCode)
        : courseName(courseName), courseCode(courseCode) {}

    void displayCourseInfo() {
        cout << "Course Name: " << courseName << "\nCourse Code: " << courseCode << endl;
    }
};

class College {
private:
    vector<Student> students;
    vector<Staff> staffMembers;
    vector<Course> courses;

public:
    void addStudent(string name, int age, string studentID, string course) {
        students.emplace_back(name, age, studentID, course);
    }

    void addStaff(string name, int age, string staffID, string department) {
        staffMembers.emplace_back(name, age, staffID, department);
    }

    void addCourse(string courseName, string courseCode) {
        courses.emplace_back(courseName, courseCode);
    }

    void displayStudents() {
        cout << "\nStudents:\n";
        for (auto& student : students) {
            student.displayInfo();
            cout << "-----------------\n";
        }
    }

    void displayStaff() {
        cout << "\nStaff Members:\n";
        for (auto& staff : staffMembers) {
            staff.displayInfo();
            cout << "-----------------\n";
        }
    }

    void displayCourses() {
        cout << "\nCourses:\n";
        for (auto& course : courses) {
            course.displayCourseInfo();
            cout << "-----------------\n";
        }
    }
};

int main() {
    College college;
    college.addStudent("Taha", 20, "2312440", "Computer Science");
    college.addStudent("Inam", 22, "2312400", "Mechanical Engineering");
    college.addStaff("Dr. Ijlal", 45, "T201", "Computer Science Department");
    college.addStaff("Dr. Tufail", 50, "T202", "Mechanical Engineering Department");
    college.addCourse("Data Structures", "CS101");
    college.addCourse("Thermodynamics", "ME102");
    college.displayStudents();
    college.displayStaff();
    college.displayCourses();
    return 0 ; 
}

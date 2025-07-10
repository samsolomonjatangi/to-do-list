# to-do-list

#include <iostream>
#include <vector>
#include <string>

using namespace std;

vector<string> tasks; // List to store tasks

void showMenu() {
    cout << "\n--- To-Do List Menu ---\n";
    cout << "1. Add Task\n";
    cout << "2. View Tasks\n";
    cout << "3. Delete Task\n";
    cout << "4. Exit\n";
    cout << "Enter your choice: ";
}

void addTask() {
    string task;
    cout << "Enter task description: ";
    cin.ignore(); // To avoid issues with getline after using cin
    getline(cin, task);
    tasks.push_back(task);
    cout << "Task added successfully!\n";
}

void viewTasks() {
    if (tasks.empty()) {
        cout << "No tasks available.\n";
        return;
    }

    cout << "\n--- Your Tasks ---\n";
    for (size_t i = 0; i < tasks.size(); ++i) {
        cout << i + 1 << ". " << tasks[i] << endl;
    }
}

void deleteTask() {
    viewTasks();
    if (tasks.empty()) return;

    int taskNumber;
    cout << "Enter task number to delete: ";
    cin >> taskNumber;

    if (taskNumber < 1 || taskNumber > static_cast<int>(tasks.size())) {
        cout << "Invalid task number.\n";
    } else {
        tasks.erase(tasks.begin() + taskNumber - 1);
        cout << "Task deleted successfully.\n";
    }
}

int main() {
    int choice;

    do {
        showMenu();
        cin >> choice;

        switch (choice) {
            case 1:
                addTask();
                break;
            case 2:
                viewTasks();
                break;
            case 3:
                deleteTask();
                break;
            case 4:
                cout << "Exiting the program. Goodbye!\n";
                break;
            default:
                cout << "Invalid choice. Please try again.\n";
        }

    } while (choice != 4);

    return 0;
}

# CS-300-Journal
A repo for my Analysis and Design class

### CODE FROM PROJECT TWO ###
int partition(vector<Course>& courses, int begin, int end) {
    int midPoint;
    string pivot;
    int lowIndex = begin;
    int highIndex = end;
    Course temp;

    midPoint = lowIndex + (highIndex - lowIndex) / 2;
    pivot = courses[midPoint].courseNumber;

    bool done = false;

    while (!done) {
        while (courses[lowIndex].courseNumber < pivot) {
            lowIndex += 1;
        }
        while (pivot < courses[highIndex].courseNumber) {
            highIndex -= 1;
        }
        if (lowIndex >= highIndex) {
            done = true;
        }
        else {
            temp = courses[lowIndex];
            courses[lowIndex] = courses[highIndex];
            courses[highIndex] = temp;

            lowIndex += 1;
            highIndex -= 1;

        }

    }
    return highIndex;
}

void quickSort(vector<Course>& courses, int begin, int end) {
    int mid = 0;
    int lowIndex = begin;
    int highIndex = end;
    int lowEndIndex;
    if (lowIndex >= highIndex) {
        return;
    }

    lowEndIndex = partition(courses, lowIndex, highIndex);

    quickSort(courses, lowIndex, lowEndIndex);
    quickSort(courses, lowEndIndex + 1, highIndex);

}

void printSortedVector(vector<Course> courses) {
    quickSort(courses, 0, courses.size() - 1);

    for (int i = 0; i < courses.size(); i++) {
        displayCourse(courses.at(i));
    }
}

### ANALYSIS FROM PROJECT ONE ###

Code	Line Cost	# of times execute	Total Cost
Open file	1	1	1
Try and catch statement that executes if there’s a format error	1	1	1
If file is open	1	1	1
For loop iterates through all the lines in the file up until the end	1	n	n
IF there is 2 or more fields in the line	1	n	n
Initialize object “courses”	1	n	n
Parser will read the first field and store it into “course number”	1	n	n
Parser will read the second field and store it into “course name” variable	1	n	n
Parser will read the third field and store it into “prerequisites” if applicable	1	n	n
Parser will read the third field and store it into “prerequisites” if applicable	1	n	n
ELSE	1	n	n
Ignore line	1	n	n
Append object “course” into vector	1	n	n
Close file	1	1	1  
                                  
Total Cost	10n + 4
Runtime	O(n)

Most data structures are well suited for storing data in large amounts but depending on the amount of data and the type of data, you might want to choose the best one that’ll fit the situation. When it comes to a vector, it benefits from being a dynamic data structure meaning that you won’t have to worry about resizing it whenever you run out of space, although this comes at a cost of utilizing more space than an array (non-dynamic data structure). A vector uses an index system making it easier to access random elements. Some disadvantages of a vector include deletion of elements, if the element that you want to delete is in the beginning then that means that the whole vector’s elements will need to be shifted to the left to fill the spot that was left empty increasing runtime. Searching for an element can also increase runtime, without knowing the index of the wanted element, you’ll have to do a linear search and compare all elements starting from the beginning, with the worst runtime if the wanted element is the one at the last index.

### JOURNAL QUESTIONS ###

1. What was the problem you were solving in the projects for this course?
In this course, the main problem that we were trying to solve is how to 
3.   

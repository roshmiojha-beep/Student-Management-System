#include<stdio.h>
#include "student.h"


int main()
{
    Student list[50];

    int currentIndex = 0;
    int option = 0;
    int i;


    printf("-----Student Management System-----");


    while(option != 4)
    {
        printf("\n-----1. Add Student---");
        printf("\n-----2. Display Student List---");
        printf("\n-----3. Search for a Student ---");
        printf("\n-----4. Exit ---");

        printf("\nEnter your choice: ");
        scanf("%d",&option);


        if(option == 1) // add student
        {
            printf("\nEnter Roll Number: ");
            scanf("%d",&list[currentIndex].roll);

            printf("Enter Name: ");
            scanf(" %[^\n]",list[currentIndex].name);

            printf("Enter Marks 1: ");
            scanf("%f",&list[currentIndex].marks1);

            printf("Enter Marks 2: ");
            scanf("%f",&list[currentIndex].marks2);

            printf("Enter Marks 3: ");
            scanf("%f",&list[currentIndex].marks3);


            list[currentIndex].totalMarks =
                list[currentIndex].marks1 +
                list[currentIndex].marks2 +
                list[currentIndex].marks3;


            list[currentIndex].averageMark =
                list[currentIndex].totalMarks / 3;


            if(list[currentIndex].averageMark >= 80)
            {
                list[currentIndex].grade = 'A';
            }
            else if(list[currentIndex].averageMark >= 60)
            {
                list[currentIndex].grade = 'B';
            }
            else if(list[currentIndex].averageMark >= 40)
            {
                list[currentIndex].grade = 'C';
            }
            else
            {
                list[currentIndex].grade = 'F';
            }


            printf("\nStudent added successfully!");

            currentIndex++;
        }


        else if(option == 2) // Display Student List
        {
            if(currentIndex == 0)
            {
                printf("\nNo students added yet.");
            }
            else
            {
                printf("\n\n-----Student List-----\n");

                for(i = 0; i < currentIndex; i++)
                {
                    printf("\nRoll Number: %d",list[i].roll);
                    printf("\nName: %s",list[i].name);
                    printf("\nMarks 1: %.2f",list[i].marks1);
                    printf("\nMarks 2: %.2f",list[i].marks2);
                    printf("\nMarks 3: %.2f",list[i].marks3);
                    printf("\nTotal Marks: %.2f",list[i].totalMarks);
                    printf("\nAverage: %.2f",list[i].averageMark);
                    printf("\nGrade: %c",list[i].grade);

                    printf("\n----------------------");
                }
            }
        }


        else if(option == 3) // Search
        {
            int roll;
            int found = 0;

            printf("\nEnter Roll Number: ");
            scanf("%d",&roll);


            for(i = 0; i < currentIndex; i++)
            {
                if(list[i].roll == roll)
                {
                    printf("\nStudent Found!");

                    printf("\nRoll Number: %d",list[i].roll);
                    printf("\nName: %s",list[i].name);
                    printf("\nMarks 1: %.2f",list[i].marks1);
                    printf("\nMarks 2: %.2f",list[i].marks2);
                    printf("\nMarks 3: %.2f",list[i].marks3);
                    printf("\nTotal Marks: %.2f",list[i].totalMarks);
                    printf("\nAverage: %.2f",list[i].averageMark);
                    printf("\nGrade: %c",list[i].grade);

                    found = 1;
                    break;
                }
            }


            if(found == 0)
            {
                printf("\nStudent not found.");
            }
        }


        else if(option == 4)
        {
            printf("\nThank you!");
        }


        else
        {
            printf("\nInvalid choice.");
        }
    }


    return 0;
}

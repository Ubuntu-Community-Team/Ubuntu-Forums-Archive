---
title: "how to convert a object file to shared object file"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by earth_tech on 2009-09-02
hello every one,
I have a  problem. I can not convert a object file to shared object file in ubuntu. The program is as follows:

#include<stdio.h>
int main()
{
   int a,b,c=0;
   printf("Enter 1 st Number:")
   scanf("%d",&a);
   printf("Enter 2 nd Number:");
   scanf("%d", &b);
   c=a+b;
   printf("The sum is %d",c);
   return 0;
}

program name is add.c
To run this program use command cc -c add.c then create a object of that file using cc -o add add.c command. After this to run the program use ./ add. Program run successfully. To convert the object file to shared object file use the following steps. These are as follows:

Step :1
Now i want to create a shared object file using add.o file. The add.o file is in earth folder which is in Desktop. To execute this object file to shared object file use cc -desktop/earth  command.
 Then shows :
cc: -E or -X required when input is form standard input

Step :2
To convert use the following command:

earth@earth: ~$ /Desktop/earth -k add.o -o add.so
Then the output is
bash: desktop/earth : No such file or directory
But i know in the earth folder there has add.o file. 

Step :3
To convert use the following command:
earth@earth:~ ld-g add.o -o add.so
Then shows
ld: warning: cannot find entry symbol_start;
defaulting to 00000000008048074
add.o: In function 'main'
add.c:(.text+0x20) : undefined reference to 'printf'
add.c:(.text+0x33) : undefined reference to 'scanf'
add.c:(.text+0x3f) : undefined reference to 'printf'
add.c:(.text+0x52) : undefined reference to 'scanf'
add.c:(.text+0x72) : undefined reference to 'printf'

Though i am a new in linux environment so i  don't know how to convert a object file to shared object file.
I can't understand what's are the errors and in which way it will solve. Please any one give me their valuable information to solve this problem.

---

### Post by stlsaint on 2009-09-02
when trying these different conversions ensure that you are in the right directory. i noticed that on one of your issue you was not in the desktop dir when trying to use a file located there.

hopefully someone else with a little more knowledge can assist in the other issues.

---


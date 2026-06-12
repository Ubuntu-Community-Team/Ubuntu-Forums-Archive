---
title: "how to execute GCC and run a &quot;.c&quot; file"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by earth_tech on 2009-09-01
**how to install GCC in ubuntu** 
   hello,
After observe the discussion between pro_net and mc4man  i am trying to install GCC in my computer. But does not install GCC. Also write a program in vi editor through terminal  then to compile use -filename.c but machine show there has no such file.

Please give me an outline how to install GCC in Ubuntu and run a c file properly.

---

### Post by mc4man on 2009-09-01
> i am trying to install GCC in my computer. But does not install GCC

Actually he was tring to install build-essential which is just an 'info' package that install some compiling tools (packages.

GCC is part of your ubuntu install so it's already installed (each ubuntu release uses a specific version as the default (system)

(search gcc in synaptic and you'll see.

Maybe post your terminal command and output plus the location of your .c file, I've got to go, but should be easily resolved

---

### Post by mechdave on 2009-09-01
The idea is to start off with a classical hello world tutorial for C. Try this one here --> [http://einstein.drexel.edu/courses/Comp_Phys/General/C_basics/]("http://einstein.drexel.edu/courses/Comp_Phys/General/C_basics/")
Taht should give you the basics...

---

### Post by earth_tech on 2009-09-01
I have a c program, want to execute to that program.
 In windows we use Turbo C as a editor to write and run after compile  the  program. In Ubuntu i am trying to write C programusing vi editor but it cannot save the file as .c extension. In vi editor it  does not accept  the symbol "#". and file also not run. In which way it can possible.

---

### Post by earth_tech on 2009-09-01
[SIZE=3]Dear mc4man,
I am a new person in Ubuntu environment. I have few problem about Ubuntu. Please help me to solve these problems.
Problem :1
I am trying to install essential package. But every time shows:
earth@earth-desktop:~$ sudo apt-get install build- essential
Reading package  lists... Done
Building dependency tree 
Reading state information...  Done
E: Couldn't find package build
But if write only
earth@earth-desktop:~$ sudo apt-get install 
then shows install success fully. Tell me the way to solve this problem.

Problem :2
Write a C program in text editor.(Application->Accessories-> Text editor).  The program is as follows:
#include<stdio.h>
#include<conio.h>
int main()
{
printf("Hello world");
return 0;
}
To compile this program  use following commands:
cc -c hello.c
 but ubuntu shows an error that there has no file or directory named conio.h . As a result the program can not run.

Problem :3

If i use gcc -hello.c it also shows an error. Ubuntu returns there has no file or directory named hello.
Please give me solutions how to recover above problems.
[/SIZE]

---

### Post by colau on 2009-09-01
> **earth_tech said:**
> [SIZE=3]Dear mc4man,
I am a new person in Ubuntu environment. I have few problem about Ubuntu. Please help me to solve these problems.
Problem :1
I am trying to install essential package. But every time shows:
earth@earth-desktop:~$ sudo apt-get install build- essential
Reading package  lists... Done
Building dependency tree 
Reading state information...  Done
E: Couldn't find package build
But if write only
earth@earth-desktop:~$ sudo apt-get install 
then shows install success fully. Tell me the way to solve this problem.

Problem :2
Write a C program in text editor.(Application->Accessories-> Text editor).  The program is as follows:
#include<stdio.h>
#include<conio.h>
int main()
{
printf("Hello world");
return 0;
}
To compile this program  use following commands:
cc -c hello.c
 but ubuntu shows an error that there has no file or directory named conio.h . As a result the program can not run.

Problem :3

If i use gcc -hello.c it also shows an error. Ubuntu returns there has no file or directory named hello.
Please give me solutions how to recover above problems.
[/SIZE]
Welcome.
```

sudo aptitude install g++
sudo aptitude search build | grep essentials

```
To compile a .c file:
```

g++ a.c -o a

```
To run that file:
```

./a

```

---

### Post by Topsiho on 2009-09-01
First thing: mc4man gave you sound advice, is not paid for it, and does not deserve at all to be shouted at like you did. However, I'll try and make some remarks that may help you further, only to be able to say what I did to you:

1. Probably the install of build-essential was blown into the wind by putting a space after the word build. I can find no other explanation.

So

sudo apt-get install build-essential (in a terminal, is that the problem?, otherwise you try using synaptic)

should do the trick. If no spaces anywhere in build-essential is to be found. Also: no s after essential.

2. I don't know whether this also applies to C, but in C++ some years ago some things were changed. If you run a program that's written for the obsolete version of C++, of which many are still be found anywhere on internet, then it will not get compiled by the newer versions of gcc. Might apply to C too, very probably.

One of these changes is that iostream.h is now iostream, and other .h files (called header files) the same. So if a .h file is not found on the system, then try it without the .h extension.

I hope for you that, if you'll now not start shouting at me, a C programmer will add his commentary to this.

Topsiho

---

### Post by mc4man on 2009-09-01
> I am trying to install essential package.
Maybe get together with pro_net, you 2 seem to be of like minds and mistakes, I'm sure you-all can work that out
[http://ubuntuforums.org/showthread.php?t=1255079](http://ubuntuforums.org/showthread.php?t=1255079)

> but ubuntu shows an error that there has no file or directory named conio.h

remove #include conio.h from your .c
> 
Ubuntu returns there has no file or directory named hello.c

Your hello.c file must be in the same directory that your terminal prompt is at. By default that would be your home dir.
If your .c ( or source or anything else you wish to run a command on) is anywhere else then either provide the full path to it in your command or cd to that dir. in the terminal

Simple ex.
Folder on Desktop named ww with a text file named test.c that contains this
```
#include <stdio.h>

int main() {
printf("Hello World!");
return 0;
}

```

> doug@doug-laptop:~$ cd [COLOR="Red"]~[/COLOR]/Desktop/ww
doug@doug-laptop:~/Desktop/[COLOR="Red"]ww$ [/COLOR]gcc -o test test.c
doug@doug-laptop:~/Desktop/ww$ ./test
Hello World!doug@doug-laptop:~/Desktop/ww$ 


Explanation of red

~  means your home dir.
ww$ - shows that I'm at the dir. prompt of ww (where the test.c file is

full path cd example not using ~ (blue would be your user name
> doug@doug-laptop:~$ cd /home/[COLOR="Blue"]doug[/COLOR]/Desktop/ww
doug@doug-laptop:~/Desktop/ww$ 


---

### Post by earth_tech on 2009-09-02
> **Topsiho said:**
> First thing: mc4man gave you sound advice, is not paid for it, and does not deserve at all to be shouted at like you did. However, I'll try and make some remarks that may help you further, only to be able to say what I did to you:

1. Probably the install of build-essential was blown into the wind by putting a space after the word build. I can find no other explanation.

So

sudo apt-get install build-essential (in a terminal, is that the problem?, otherwise you try using synaptic)

should do the trick. If no spaces anywhere in build-essential is to be found. Also: no s after essential.

2. I don't know whether this also applies to C, but in C++ some years ago some things were changed. If you run a program that's written for the obsolete version of C++, of which many are still be found anywhere on internet, then it will not get compiled by the newer versions of gcc. Might apply to C too, very probably.

One of these changes is that iostream.h is now iostream, and other .h files (called header files) the same. So if a .h file is not found on the system, then try it without the .h extension.

I hope for you that, if you'll now not start shouting at me, a C programmer will add his commentary to this.

Topsiho

Thanks
Topsiho for your kind information.

---

### Post by earth_tech on 2009-09-02
hello every one,
I want to inform you that my program run successfully in ubuntu. Using command cc -c hello.c (file name) then use the command cc - o hello hello.c for create object of that program file. After create the object to run the program use command ./ hello. My question is object file created but in which way i can create shared object file of the file. Please give me details way to solve the problem.

---

### Post by Topsiho on 2009-09-02
> **earth_tech said:**
> hello every one,
 After create the object to run the program use command ./ hello. 

First: Thanks for reacting to my post the way you did. It's great.

Next: There again is a space in ./ hello where no space should be :)
So it is ./hello. This is for all who read this thread not to get confused :)

I am sorry I can not answer your next question.

Topsiho

---


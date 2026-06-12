---
title: "[SOLVED] javac compiler help"
date: 2008-08-19
forum: General Help
---

### Post by greenco on 2008-08-19
I used the Ubuntu 8.04 Synaptic Package Manager to install the "sun-java6-jdk" and all of the additional packages that went with it. I would like to learn to program with java, but I can't get the simplist program (helloworld.java) to compile. Here are three examples that I have managed to run in the terminal;

I ran this one to make sure I had the correct version installed.

coleman@coleman-desktop:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
coleman@coleman-desktop:~$ 


I made a folder in my home folder and named it " java ", to hold my java code. I used gedit and typed in the "helloworld.java" code and saved it in the java folder, as shown in this one.

coleman@coleman-desktop:~$ cd
coleman@coleman-desktop:~$ cd java
coleman@coleman-desktop:~/java$ dir
helloworld.Java
coleman@coleman-desktop:~/java$ 


I then tried to compile it with the "javac" compiler and got an error that told me it could not find the helloworld.java file, as shown in this one.

coleman@coleman-desktop:~$ cd
coleman@coleman-desktop:~$ cd java
coleman@coleman-desktop:~/java$ javac helloworld.java
javac: file not found: helloworld.java
Usage: javac <options> <source files>
use -help for a list of possible options
coleman@coleman-desktop:~/java$ 

From all of the examples that I have found this should haved work. 

1. Do I need to be in a different folder or directory and run javac from there?

2. What terminal commands do I use to find the path to the "javac" compiler and the java jdk?

From what I have found on all of my Google searches, about this subject, there are lots of folks that can't get it to work. Can anyone point me in the right direction, to solve this?

---

### Post by indiv on 2008-08-19
Filenames are case sensitive.  I see that you've named the file **helloworld.Java** but you're trying to compile **helloworld.java**.  I'd stick with lowercase names and do this to fix it:

mv helloworld.Java helloworld.java
javac helloworld.java

Also, the shell has filename completion when you press tab.  Try **javac hello[tab]**, where [tab] is where you hit the tab key.  If the file exists, the shell will expand it for you.  That's a good way of finding out whether the file or directory you're typing is really there.

To answer point number 2, you can type **which javac** or **whereis javac** to find the java compiler.  **find / -name java** could help you locate the jdk.

---

### Post by greenco on 2008-08-19
Thanks indiv!!!

I have looked at the filename spelling for hours and I did not pick up on the capital " J " in one spot and a lower case " j "in the other. I might look into finding another font <GRIN>. I also had another problem, in the code itself. I had used a  mixed case in the public statement and had to change it to all lower case and now it compiles. I am going to add your tips to my archives for the future. Now on to more complicated code.
Thanks a million!!

---


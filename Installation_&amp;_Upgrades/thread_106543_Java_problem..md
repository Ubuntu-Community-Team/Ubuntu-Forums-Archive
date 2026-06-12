---
title: "Java problem."
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by rlsuth on 2005-12-20
Firstly, I have no idea what I'm doing as I've just installed Ubuntu for the first time.

Having got that out of the way: I tried to install Java, as it is required for a program that I want to run under Linux, to work. The program I am trying to execute is called: Shredder Chess ([http://www.shredderchess.com/chess-download/free-demo-download/download-shredder-classic-linux.html](http://www.shredderchess.com/chess-download/free-demo-download/download-shredder-classic-linux.html))

I cant get this to work. 

Is there a way I can check to see if my Java install was successful or not?

---

### Post by ape on 2005-12-21
okay. downloaded the program and it worked okay for me.  I've got the Sun j2sdk 1.5.0_06 installed.

What java package have you installed?

What does the command `which java` return?

What is the output of `java -version`?

---

### Post by rlsuth on 2005-12-21
Thanks for the reply.

I tried to install the same package as you have. Well, it was called "jre-1_5_0_06-linux-amd64.bin" anyway.
When I enter "Which java" in the terminal window, I only get "/usr/bin/java" back while "java -version" returns "gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)".

I assume that this means my java installation didn't work?

---

### Post by kaamos on 2005-12-21
```
sudo update-alternatives --config java
```
Try if this gives you the alternative to choose the sun jre.

---

### Post by rlsuth on 2005-12-21
[QUOTE=kaamos]```
sudo update-alternatives --config java
```
Try if this gives you the alternative to choose the sun jre.[/QUOTE]



Thank you so much. I did this and everything now works. 

It's going to take a while to learn what exactly I've done, but it's encouraging that, with your help, I got something to work :).

---

### Post by Zaventh on 2005-12-21
I have the same problem with another jar file... expect when I run the alternatives command I don't see my java installation from sun as an option there. Why not? I installed it per the instructions on their website...

---

### Post by ape on 2005-12-22
Ubuntu will no nothing of the version of java you install using the j2sdk*.bin file from sun.  You need to do the following:

  1. Download the j2sdk*.bin file from sun (as you've already done).

  2. Make sure that you have installed the java-package and fakeroot packages.

  3. run the following command:

          fakeroot make-jpkg <path to the j2sdk*.bin file from sun>

  This will produce a .deb archive of the sun j2sdk distribution.  You then install this using dpkg -i <.deb file>.  Now you will be able to see it when you issue the`update-alternatives --config java` command.

---


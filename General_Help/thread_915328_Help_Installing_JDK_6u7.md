---
title: "Help Installing JDK 6u7"
date: 2008-09-09
forum: General Help
---

### Post by Maxcore on 2008-09-09
So the past few days have been absolute computer hell. I am at college and have an HP laptop and I accidentally dropped my alarm clock on it and broke the hard drive that had my operating system on it. I installed Ubuntu on the other and I love it, but I am having some trouble installing the JDK on it which I need for my computer science homework which is due tomorrow lol. I downloaded the jdk 6u7 from the java website and I installed it using the instructions found at [http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html) but I got this error when installing:

> Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jdk-6u7-linux-i586.rpm  
  inflating: sun-javadb-common-10.3.1-4.1.i386.rpm  
  inflating: sun-javadb-core-10.3.1-4.1.i386.rpm  
  inflating: sun-javadb-client-10.3.1-4.1.i386.rpm  
  inflating: sun-javadb-demo-10.3.1-4.1.i386.rpm  
  inflating: sun-javadb-docs-10.3.1-4.1.i386.rpm  
  inflating: sun-javadb-javadoc-10.3.1-4.1.i386.rpm  
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found
Installing JavaDB
./jdk-6u7-linux-i586-rpm.bin: 610: rpm: not found


does anyone know how to install the jdk? any help would be so awesome, thanks a lot.

---

### Post by IllegalCharacter on 2008-09-09
Looks like you downloaded the RPM, which is the RedHat package format. You can use RPMs in Ubuntu, but it's a pain in the ***.

You can install Java through the package manager. Here's the steps:

1) Go to System->Administration->Synaptic Package Manager
2) Type your password when it asks
3) Click Search, choose "Name" for the "Look In" field, and then search for "sun-java6-jre"
4) There should only be one result, so double click that one and accept any dependencies it wants to install.
5) Install!

If you want to actually program in Java, you should install "sun-java6-jdk".

---

### Post by Maxcore on 2008-09-09
Wow thank you so much, you are a life saver (literally)!!!

---

### Post by suzieboy on 2008-11-06
for real...this was helpful..thx...hell this was even easier than installing in WinXP ...i can now finish my assignment...

---


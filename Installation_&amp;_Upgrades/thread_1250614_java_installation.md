---
title: "java installation"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by mulligan on 2009-08-26
hi i am trying to install java jre and jdk onto ubuntu. i have had some success with the sudo apt-get install function. however it is now stating. 

morgan@morgan-desktop:~$ sudo apr-get install sun-java6-jre
[sudo] password for morgan: 
sudo: apr-get: command not found
morgan@morgan-desktop:~$ sudo apt-get install sun-java6-jre
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
morgan@morgan-desktop:~$ 

i am not sure if i have java or not can you tell me how to check and how to download properly and also how to fix the problem the above message says i have.

thank you in advance. mulligan.

---

### Post by mulligan on 2009-08-26
in addition i tried to find out if i had java this is what is showed me.

morgan@morgan-desktop:~$ javac No.java
The program 'javac' can be found in the following packages:
 * java-gcj-compat-dev
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * sun-java6-jdk
 * jikes-kaffe
 * openjdk-6-jdk
 * ecj
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * jikes-sun
Try: sudo apt-get install <selected package>
bash: javac: command not found
morgan@morgan-desktop:~$ java No
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
morgan@morgan-desktop:~$ 

is that helpful. thanks.

---

### Post by oldos2er on 2009-08-26
Run ```
sudo dpkg --configure -a
``` in a terminal. When the Java license agreement comes up, use Tab to highlight OK then press Enter.

---

### Post by mulligan on 2009-08-26
ok i did what you said and then i tried to install java again. this time i got this.

morgan@morgan-desktop:~$ sudo apt-get install sun-java6-jdk sun-java6-jre
[sudo] password for morgan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-14-0ubuntu1.8.04) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-14-0ubuntu1.8.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-14-0ubuntu1.8.04) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
morgan@morgan-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
morgan@morgan-desktop:~$

---

### Post by ibutho on 2009-08-26
You need to run
```
sudo apt-get -f install
```
In Ubuntu if you see the warnings about not being "root", prefix any suggested commands with sudo. I guess when the package was ported from Debian someone forgot to change the command so that it reads as "sudo apt-get -f install" on Ubuntu based systems.

---

### Post by mulligan on 2009-08-26
ok i think i have it now i got it to run and tabed and passed the agreement. do you know how i can check that i have it on my system.

---

### Post by mulligan on 2009-08-26
i found a link that told me how to do it. can you confirm it have it on my system.

this is what it showed me when i searched. thank you.

morgan@morgan-desktop:~$ apt-cache search jdk
libcommons-lang-java - Extension of the java.lang package
libitext-java - Java Library to generate PDF on the Fly
libpg-java - Java database (JDBC) driver for PostgreSQL
jde - JDEE, Java Development Environment for Emacs(en)
free-java-sdk - Complete Java SDK environment consisting of free Java tools
icepick - java toolchain built from OpenJDK sources
icepick-gcj - java toolchain built from OpenJDK sources (native library)
japitools - Java API compatibility testing tools
kaffe - A JVM to run Java bytecode
libcommons-launcher-java - cross platform java application launcher
libhibernate-commons-annotations-java - Hibernate Commons Annotations
libicu4j-java - Library for unicode support and internalisation
libjboss-common-java - The JBoss Common Project
libnb-javaparser-java - Parser for the Java language which is good for use in tools
librxtx-java - Full Java CommAPI implementation
libtrove-java - high performance collections for java
libtrove-java-doc - high performance collections for java
libwagon-java - tools to manage Maven artifacts and deployment
mauve - free test suite for the Java Class libraries
mmake - Makefile generator for Java programs
usepackage - utility to manage environment variables from within dotfiles
openoffice.org-gcj - OpenOffice.orgs Java libraries (native for use with GIJ)
sun-java5-bin - Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture dependent files)
sun-java5-demo - Sun Java(TM) Development Kit (JDK) 5.0 demos and examples
sun-java5-doc - Sun JDK(TM) Documention -- integration installer
sun-java5-jdk - Sun Java(TM) Development Kit (JDK) 5.0
sun-java5-jre - Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture independent files)
sun-java5-source - Sun Java(TM) Development Kit (JDK) 5.0 source files
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-doc - Sun JDK(TM) Documention -- integration installer
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
icedtea-java7-jdk - Java development kit based on OpenJDK (transitional package)
icedtea-java7-jre - Java runtime based on OpenJDK (transitional package)
openjdk-6-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-6-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-6-doc - OpenJDK Development Kit (JDK) documentation
openjdk-6-jdk - OpenJDK Development Kit (JDK)
openjdk-6-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-6-jre-lib - OpenJDK Java runtime (architecture independent libraries)
openjdk-6-source - OpenJDK Development Kit (JDK) source files
morgan@morgan-desktop:~$

---

### Post by ibutho on 2009-08-26
To check is java is installed, try
```
java -version
```

---

### Post by mulligan on 2009-08-26
this is what i got it seems promising is it correct.

java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)
morgan@morgan-desktop:~$

---

### Post by ibutho on 2009-08-26
Thats correct. I get the same output on my Linux Mint 7 (Ubuntu 9.04) based computer.

---

### Post by mulligan on 2009-08-26
thanks for all your help. cheers.

---


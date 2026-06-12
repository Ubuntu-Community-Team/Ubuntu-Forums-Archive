---
title: "Problem in Installation of Glassfish"
date: 2008-07-12
forum: General Help
---

### Post by annamalai.gurusami on 2008-07-12
Hi All.

I am trying to install Glassfish.  I am following the instructions in the URL

[https://glassfish.dev.java.net/downloads/v2ur2-b04.html](https://glassfish.dev.java.net/downloads/v2ur2-b04.html)

I downloaded the package glassfish-installer-v2ur2-b04-linux.jar.  When the run the ant program I got the error that tools.jar is not found. What could be the problem?  How to fix it?  The complete error message is listed below.  

(begin-quote)

odali@dragonfly:~/glassfish$ lib/ant/bin/ant -f setup.xml 
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-sun-1.6.0.06/lib/tools.jar
Buildfile: setup.xml

all:

get.java.home:

setup.init:

check-java:

get.java.home:

setup.init:

validate-java:
     [echo] Current Java Version 1.6.0_06

BUILD FAILED
/home/odali/glassfish/setup.xml:156: The following error occurred while executing this line:
/home/odali/glassfish/setup.xml:136: The following error occurred while executing this line:
/home/odali/glassfish/setup.xml:132: Please set java.home to a JDK installation

Total time: 1 second
odali@dragonfly:~/glassfish$ 

(end-quote)

Note that the java.home is correctly identified as /usr/lib/jvm/java-6-sun-1.6.0.06

Rgds,
anna

---

### Post by annamalai.gurusami on 2008-07-12
The problem was only JRE was installed.  No JDK was installed.  So I installed JDK using the command '$ sudo apt-get install sun-java6-jdk'.  Now it is working correctly.  Thank you.

---


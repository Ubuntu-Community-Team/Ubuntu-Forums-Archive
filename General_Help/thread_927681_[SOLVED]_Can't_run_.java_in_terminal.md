---
title: "[SOLVED] Can't run .java in terminal"
date: 2008-09-23
forum: General Help
---

### Post by Mustardo on 2008-09-23
Hello to all

I get an error when I try to run a java file I have recently written and compiled in emacs

when i type in terminal " java filename.java "

Exception in thread "main" java.lang.NoClassDefFoundError: StudentApp/java
Caused by: java.lang.ClassNotFoundException: StudentApp.java
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: StudentApp.java. Program will exit.


Thank you to anybody who can help me.

---

### Post by SyL on 2008-09-23
> **Mustardo said:**
> Hello to all

I get an error when I try to run a java file I have recently written and compiled in emacs

when i type in terminal " java filename.java "

Exception in thread "main" java.lang.NoClassDefFoundError: StudentApp/java
Caused by: java.lang.ClassNotFoundException: StudentApp.java
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: StudentApp.java. Program will exit.


Thank you to anybody who can help me.



You need to add StudentApp.java in your classpath

---

### Post by bogdan.veringioiu on 2008-09-23
Hi.

First you have to compile the source .java file:

javac filename.java

Then you obtain a .class file (StudentApp.class probably), and you can run it:

java StudentApp

Regards

---

### Post by issih on 2008-09-23
um...unless things have changed since I last used java, you are doing it wrong.

the .java file is your source code...when you compile that it turns into bytecode in a .class file of the same name. When you run the program using java at the command line you need to include the class files in the classpath (hence the name) and then specify the location of the entry point (class with static Main method) in terms of package and class name, e.g for running imageJ you do:

```
java ij.ImageJ
```

because the class ImageJ is the entry point and its in the package ij.

You must either launch from the directory containing the class files necessary to run the program or include the directory in the classpath via the command line options, I think its -cp...look at the man page

Hope that helps

---

### Post by Mustardo on 2008-09-24
Thanks everybody for your help.  

Would not run due to a runtime error caused by my code.

Also when calling from the directory within a terminal it should be 

**java <filename>**

not java <filename.extension>

---


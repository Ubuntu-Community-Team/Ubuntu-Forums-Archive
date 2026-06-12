---
title: "Running Java"
date: 2005-11-09
forum: General Help
---

### Post by b_chris on 2005-11-09
Hello,

I'm trying to run  A JAVA app with the command 'Java [program name], but I get the following error:

Exception in thread "main" java.lang.NoClassDefFoundError: humanitrader
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: humanitrader not found in gnu.g
cj.runtime.SystemClassLoader{urls=[file:./,file:./], parent=gnu.gcj.runtime.                                       ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.s                                       o.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/l                                       ibgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.                                       6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoad                                       er) (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)


Does this mean I need to do some linking??

regards.

---

### Post by mneptok on 2005-11-09
Try "java -jar /path/to/app.jar"

---

### Post by b_chris on 2005-11-09
HHHHmmmmmm, now I get this error:

Failed to load Main-Class manifest attribute from humaitrader


Thanks for you help too.

regards.

---

### Post by Romzhv on 2005-11-09
Starting Java program is simple. Making it work - a bit complicated.
Usually Java "program" is not in binary executable form. Source code (*.java) is compiled into *.class file (or files). The *.jar file is just an zipped archived file with several *.class files put there in certain order (for example several folders containing another sub-folders etc etc). 
When you try to run it, like "java -jar file1.jar", it searches for some startup *.class file inside this *.jar. Usually all the job done by inspecting the manifest file with all settings about current *.jar. When it is found it searches for main(..) method or in more simple words, certain place where to start this class. When it's started, everything is ok.
But!
Sometimes jar files contain classes without startups. They are considered as libraries. As you probably know, you cannot run libraries. But you can use them to make another Java programs (sometimes these classes contain useful functions).
But! (again..:razz:)
Sometimes jar files contain classes where startup class is kinda tricky to make running. In that case you have to know wich class contains the startup point you need.

Hope this enlighted you.

---

### Post by Romzhv on 2005-11-09
Oh, yes. About the exceptions. These exceptions are specific situations where Java program does not want to do something bad to the system. In particular case it shows that there is some part of your program is missing. Usually Java program consists of classes. They made in a very special way so that a Java programmer could re-use several standard classes (usually there are a whole bunch of standard classes in every Java distribution). Some examples are: java.net.* classes, java.lang.*, etc. The point of my "lecture" here is simple. I suspect that there is some difference between libgcj (of GNU Java) and for example, Sun's java libraries or IBM's... they should all be standard ones... but seems they dont.
Another idea wich is the most probabe - the java runner ("java someprogram") does not "know" about where are some classes your program needs.
My suggestion for the last one - to try different java set (personally I would use Sun's, ver 1.5 or better instead of GNU's) and/or check for path to needed classes. It is now obsolete, but sometimes helps to set your CLASSPATH system variable like: CLASSPATH=.;/path/to/classlib1.jar;/path/to/another/classlib2.jar;/just/simple.class
Or to run "java" -classpath /path/to/your/libs.jar;%CLASSPATH%;/some/other/path/to/libs2.jar yourprogram.class" or "... -jar yourprogram.jar"

---


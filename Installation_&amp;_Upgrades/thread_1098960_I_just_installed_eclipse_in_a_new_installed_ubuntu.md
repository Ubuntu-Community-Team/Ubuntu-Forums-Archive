---
title: "I just installed eclipse in a new installed ubuntu system.JVM terminated.Exit Code=1."
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by the_analyzer on 2009-03-17
While opens, I got the message error containing:

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 1e8012
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 


After getting this I installed Java Runtime Environment, cause I thought it would be the problem (its a fresh system, just formated, running ubuntu)
help me please..

---

### Post by jespdj on 2009-03-17
Ok... You are using GNU Java. That is not going to work - GNU Java is old, slow, incomplete and incompatible, and Eclipse does not work properly with it. Install Sun Java 6:
```
sudo apt-get install sun-java6-jdk
```
Then use the following command to make sure (or set) Sun Java 6 as the default Java used on your system:
```
sudo update-alternatives --config java
```

---

### Post by the_analyzer on 2009-03-17
thnx man, Ill give a try. 
But Should I uninstall this java (eclipse) that I have?

---

### Post by bapoumba on 2009-03-17
Moved to Installation & Upgrades.

---

### Post by the_analyzer on 2009-03-17
> **jespdj said:**
> Ok... You are using GNU Java. That is not going to work - GNU Java is old, slow, incomplete and incompatible, and Eclipse does not work properly with it. Install Sun Java 6:
```
sudo apt-get install sun-java6-jdk
```
Then use the following command to make sure (or set) Sun Java 6 as the default Java used on your system:
```
sudo update-alternatives --config java
```

man I installed that, what should I do now, it is installed sth called Jconsole. What can I do with that? 
I want eclipse, some kind of IDE that I can write JAVA programs, 
help me guys please. :)
Im a beginner regarding development in linux.

best

---

### Post by lvleph on 2009-03-17
That was to configure Java. Eclipse is the IDE. Use Eclipse after properly configuring the JDK.

---

### Post by jespdj on 2009-03-18
> **the_analyzer said:**
> man I installed that, what should I do now, it is installed sth called Jconsole. What can I do with that? 
I want eclipse, some kind of IDE that I can write JAVA programs, 
help me guys please. :)
Eclipse is itself a program written in Java. To be able to run Eclipse, you need a good version of Java (and not GNU Java, which you were using). Those instructions were to install the right version of Java.

After doing this, you should be able to start Eclipse without problems. There is no need to re-install Eclipse if you already had it installed.

---

### Post by the_analyzer on 2009-03-18
nope, stil it isnt working, the result is the same window. 

what about this.
```
sudo update-alternatives --config java
```
when I run this, it shows me enter input or sth, I dont know what to write, maybe it isnt the default yet. I dont know.

help me please, I really need this, I mean, its very strange,
I install ubuntu, and then from add/new I add Eclipse, why that shouldnt work, or they should write a tutorial for this. god damn. :)

---

### Post by jespdj on 2009-03-18
The update-alternatives command shows you a menu in which you can select the default Java. Select Sun Java. Look closely at what is on the screen and try to understand it - don't just blindly copy and paste commands without thinking.

*edit*: If you don't want to deal with the menu, do this to directly select Sun Java as the default Java:
```
sudo update-java-alternatives -s java-6-sun
```
See [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by the_analyzer on 2009-03-18
again, the same. 
Here is a screenshot?

Ill start reading your link anyway.

thnx

---

### Post by the_analyzer on 2009-03-18
anyway, guys thnx for helping, I found the solution, 

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

I had to install OpenJDK Java Runtime. 

:)

Im happy

---

### Post by NilsThorell on 2009-11-19
How do I uninstall Eclipse completely from Ubuntu?
I had Eclipse Ganymede 3.4.2 working but I tried to install Galileo 3.5 but now nothing works.
I want to remove all Eclipse versions and restart from scratch.

(I have the impression that Ganymede is safer and easier to get working, so I'll stick to  that)

---


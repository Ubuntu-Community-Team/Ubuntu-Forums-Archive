---
title: "Java  on Ubuntu"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by tom12167 on 2009-02-26
I'm deploying a Java Application and wonder why Java is not installed on Ubuntu. Java is only in the Ubuntu installer for online installation. My customers just want the application to start, a lot of them they are not experienced enough or simply not willing to do system configurations before.

---

### Post by stumbleUpon on 2009-02-26
Ubuntu does not have sun java by default, but has gcj

"The GCJ flavor of Java is installed as default..."

quote from this page [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

hoever you can install any java you want, and it is quite easy. instructions on this page [https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)

---

### Post by tom12167 on 2009-02-26
I fear GCJ may not be able to handle a Java JNLP file. When clicking on the JNLP file in Firefox it asks to save the file instead of opening it with javaws. Maybe it's simply a question of file type recognition.

---

### Post by stumbleUpon on 2009-02-26
I think you need sun java web start to handle jnlp files. I dont know much here.

I have sun-java-6 installed and when i click on a jnlp file, it takes web start as the default application to open it.

So maybe you can try installing sun java and see if it works for you.

---

### Post by tom12167 on 2009-02-26
With sun java 6 the jnlpfile starts the application and creates an icon on the desktop, this is ok. For recommending a certain Linux distribution to my customers it should have a preinstalled java that can handle a jnlpfile.

---

### Post by jespdj on 2009-02-26
GNU Java is obsolete, slow and not compatible with recent Sun Java versions. Don't use it - your program will most likely not run well on it.

There are two options: OpenJDK Java or Sun Java. OpenJDK Java is Sun's project to make their Java implementation open source; it's 95% compatible with Sun Java 6. For compatibility, Sun Java 6 is the best version of Java you could choose.

There's no Java installed by default on Ubuntu, so if it's a requirement that the user doesn't have to do anything and that the JNLP file should just work on a freshly installed Ubuntu, it's not going to work.

---

### Post by tom12167 on 2009-02-26
Thank you for clearing this situation, full Java installation is left to the user - for whatever reasons.

---

### Post by SoniXuS on 2009-02-26
You could create a script to run instead of the java file. The script can check if java is installed, if not, warn the user and install java, run it afterwards...

If there is one thing that needs to be replaced or removed, it's GCJ. It lacks a lot of stuff...

---


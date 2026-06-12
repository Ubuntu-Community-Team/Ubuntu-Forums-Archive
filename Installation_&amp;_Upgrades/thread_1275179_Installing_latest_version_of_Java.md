---
title: "Installing latest version of Java"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by COMTIBoy on 2009-09-25
I did a new install of Ubuntu 9.04 on my machine and I'm having trouble loading the latest version of Java. 

suaro@suaro-desktop:/usr$ java -version
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Client VM (build 14.2-b01, mixed mode, sharing)
suaro@suaro-desktop:/usr$ 

The java site ([http://www.java.com/en/](http://www.java.com/en/)) shows Version 6 Update 16 is the latest.  

I used Synaptic Package Manager and I'm certain I installed version 6 (some rev); however; when I go to the Java webpage , it show's that I'm running 1.6.0_16 and not passing the test :(  . 

I'm pretty certain I selected:

**Sun Java(TM) Runtime Environment (JRE) 6** (architecture dependent files)
The Sun Java Platform Standard Edition Runtime Environment (JRE) 6
 contains the Java virtual machine, runtime class libraries, and
Java application launcher that are necessary to run programs written
in the Java progamming language. It is not a development environment and
doesn't contain development tools such as compilers or debuggers.
For development tools, see the Java Development Kit JDK(TM) 6
(package sun-java6-jdk).


How can I get my broswer to pass the Java test ? :)

I know the version I installed from Synaptic occured because my Chess client program (Jin 2.14.1) wouldn't run until I installed the Java mentioned above.  Curious to know why my browser shows a lesser version number..  I'm running gnome (not kde).
Thanks all !

---

### Post by COMTIBoy on 2009-09-25
I verified that I have the following packages installed:

sun-java6-bin
sun-java6-jre
sun-java6-jdk
sun-java6-plugin
java-common

Any ideas greatly appreciated.

---

### Post by falconindy on 2009-09-25
> **COMTIBoy said:**
> I verified that I have the following packages installed:

sun-java6-bin
sun-java6-jre
**sun-java6-jdk**
sun-java6-plugin
java-common

Any ideas greatly appreciated.
Not going to need the jdk if you don't have plans to write Java code.

---

### Post by COMTIBoy on 2009-09-26
Wonder if I posted this in the wrong forum  section ?
Anybody have any ideas ?

---

### Post by Arup on 2009-09-26
The one you are using is the latest. I installed Java from Synaptic and my java -version command gives me java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) 64-Bit Server VM (build 14.2-b01, mixed mode)

This is exactly the version thats listed on Sun site.

---

### Post by COMTIBoy on 2009-09-26
Thanks!

---


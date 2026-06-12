---
title: "Java Installation"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by arnab_das on 2009-07-30
how do i know if my version of ubuntu has java installed?

and if i find its not, then how do i install it?

---

### Post by birdwin on 2009-07-30
Open a Terminal (Applications->Accessories) and run the following:

dpkg -l | grep java

This will show you what versions of the Java packages you have installed, if any. If nothing shows up, run one of the following:

sudo apt-get install sun-java6-plugin (Firefox plugin, also installs a JRE)
sudo apt-get install sun-java6-jre (Just the JRE, so you can run Java stuff)
sudo apt-get install sun-java6-jdk (Installs the JDK in addition to the JRE, so you can also compile Java stuff)

There are closer-to-FOSS alternatives (openjdk-6-jre and variants, icedtea6-plugin) if the Sun EULA bothers you, but I've never tried them.

---

### Post by jerrrys on 2009-07-30
answer to both questions

System>Administration>Synaptic Package Manager

if not installed;  install java plugin.

make that sun java

and nothing wrong with the above, was typing while this was posted

---

### Post by arnab_das on 2009-07-31
thanks for the replies folks.

the thing is when i typed the "dpkg -l | grep java" in the terminal i found that java was installed as there were names of java versions and stuff on the screen.

however i'm unable to run any java applet on my firefox! why is that? plz help.

when i type "java -version" on the terminal, this is what i get:

java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu10)
OpenJDK Client VM (build 14.0-b08, mixed mode, sharing)

---

### Post by birdwin on 2009-07-31
Try running this:

sudo apt-get install icedtea6-plugin

then restart Firefox and let us know.

---


---
title: "Installing JDK 1.6, but mixed with JDK 1.5"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by Dave232 on 2009-07-20
I can't get Java installed correctly...

I've been running Ubuntu 8.04, using Eclipse and writing Java code.  I recently installed Ubuntu 9.04 (fresh install for 9.04, all files backed up elsewhere).  I'm happy with most of 9.04.  I tried installing Java 1.6 through several methods (synaptic and command line).  The Java binaries are soft links to /etc/alternatives (Really? That seems like an odd place.)

$ java -version  ==>  "java version 1.5.0"
$ javac -version  ==>  "javac 1.6.0_14"
$ which java  ==>  /usr/bin/java
$ which javac  ==>  /usr/bin/javac
$ ls -l /usr/bin/java  ==>  /etc/alternatives/java
$ ls -l /usr/bin/javac  ==>  /etc/alternatives/javac

It looks like I have a mix of 1.5 and 1.6.  I keep trying to remove everything Java so that I can install a (single) instance of 1.6.  But, I keep getting the same (mixed) results.  I assume that I don't want any of 1.5, and that I want (only) 1.6 installed.

The resulting behavior is that my Java programs don't run.  Swing based programs, buttons simply don't work, things hang.

Suggestions?

Dave.

---

### Post by QIII on 2009-07-20
It looks like you were able to install the latest Java compiler OK.  That comes out of the JDK.

Could you post the command line text you used to install the Java jre, plugin and bin?

The Repos now have 1.6 update 14, so if you have updated you should be able to get update 14.

---

### Post by kostkon on 2009-07-20
You can set a default. Thus, try this:

Open a terminal and give
```
sudo update-java-alternatives -l
```
just to check the available JVMs and then give
```
sudo update-alternatives --config java
```
and follow the prompts.

Hope that helps somehow.

---


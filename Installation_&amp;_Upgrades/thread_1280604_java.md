---
title: "java"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by jfmxl on 2009-10-02
Hi,

I used to use jEdit, a java editor that works quite well. But the support for unicode, specifically Thai, fonts disappeared the other day.

jfl@ws3:~$ which java
/usr/bin/java
jfl@ws3:~$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 2009-08-12 03:22 /usr/bin/java -> /etc/alternatives/java
jfl@ws3:~$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 36 2009-10-02 20:28 /etc/alternatives/java -> /usr/lib/jvm/java-6-openjdk/jre/bin/java
jfl@ws3:~$ sudo apt-get install libfonts-java sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfonts-java is already the newest version.
sun-java6-fonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jfl@ws3:~$ 

I've tried unlinking and relinking to

 /usr/lib/jvm/java-6-sun-1.6.0.16/jre/bin/java

No difference.

This used to work.

Any suggestions?

---


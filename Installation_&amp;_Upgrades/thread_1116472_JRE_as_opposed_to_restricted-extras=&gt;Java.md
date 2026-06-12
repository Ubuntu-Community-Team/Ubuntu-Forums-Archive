---
title: "JRE as opposed to restricted-extras=&gt;Java"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2009-04-04
In a perfect world, I'd be posting to a kubuntu forum, but I note
that the site for kubuntu is down.
I'm using kubuntu 7.10. Java 1.5 was installed via kubuntu-restricted-extras
if memory serves me. Now I'm considering installing a piece of software
that distinguishes between the java the "comes with" ubuntu and the java
that is part of the Java Runtime Environment (JRE). 

Is it possible that the JRE could create problems for existing applications
that I have already installed?

Any pointers to discussions on this topic would be appreciated.
thanks
tim

---

### Post by tommcd on 2009-04-05
First thing:
Ubuntu 7.10 will not be supported after April 18, 2009. 
[http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)
You should do a clean install of Ubuntu 8.04 LTS, 8.10, or 9.04 beta.
Second:
I'm pretty sure the ubuntu-restricted-extras meta package installs the Sun Java Runtime environment package.
To see which java you have installed, open a terminal and run:
```
aptitude search jre
```
A **p** before the package name means that it is purged (i.e., not installed). A **i** before the package name means that it is installed.

---

### Post by vandorjw on 2009-04-05
If you have java installed somewhere due to the package manager, and you decide to download jre 6u12 (or something to the like) and install or unpack it somewhere else, it will not affect your current programs and applications. 

UNLESS ofcourse you install in the same directory as the current java version is installed to.

For example:
if Java is installed in /usr/local/java
and you decide to install another java enviroment in /opt/jre

Existing programs have no problems.

BUT...
if Java is installed in /usr/local/java
and you decide to install another java enviroment in /usr/local/java

and overwrite old files, you might have a problem.

Cheers - CC7

(I hope this answers your question)

---

### Post by tim042849 on 2009-04-05
> **tommcd said:**
>  
You should do a clean install of Ubuntu 8.04 LTS, 8.10, or 9.04 beta.

I'm aware of the pending change - so I'll tackle the java issue after 
the upgrade. BTW: I've upgraded in the past by retaining my /home
partition (/home and / are on different mountpoints). Would that still
be OK?
Thanks
Tim

---

### Post by vandorjw on 2009-04-06
Yes, you should be ok.

---


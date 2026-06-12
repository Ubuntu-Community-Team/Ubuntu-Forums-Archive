---
title: "Class Path (Environment Varialbles)"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by kicksave on 2008-12-20
I am slowly testing my way into the Linux world.  I basically use my computer to program Java (games/robots/mini-aps) and some web design.

I followed an awesome how-to by a forum member named Phossal but it had a small bit of info missing (How to set variable paths).

I installed the Java jdk in   /usr/lib/Java6u1

I installed Eclipse in    /usr/lib/eclipse

When I went to the command line and ran Eclipse an error "Can not find JDK or JRE...  looked in: usr/lib/eclipse/jre/bin/java"  came about.  

I know it is because I need to set a path but I do not know how to do this.  

I actually did a bit of butchery and dragged the JRE folder from Java6u1 and Eclipse works (but this is ugly).

If you do reply to this your patience and specificity is appreciated.

---

### Post by taurus on 2008-12-20
You mean you want to add this directory to your PATH, /usr/lib/eclipse/jre/bin?  If that's what you want, you can edit ~/.bashrc

```
mousepad ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:/usr/lib/eclipse/jre/bin
export PATH
```
Save it and close gedit window.  Then run

```
source ~/.bashrc
```
But if you want to configure java on your machine, then what's the output of this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by sarang on 2008-12-20
I suggest not installing java from sun but instead installing sun's java from the repositories - it is sun java, but packaged appropriately for ubuntu. Alternatively, you can install the openjdk-6 which recently achieved full compliance with sun java.

In general, I prefer software from the repositories to direct 3rd party software.

First enable the multiverse component of the repositories:  

```
 sudo software-properties-gtk 
```

and enable the multiverse component.

Remove all of sun's things that you installed and then install software from the repository:

```
sudo apt-get install sun-java6-jdk sun-java6-plugin 
```

or 

```
sudo apt-get install openjdk-6-jdk icedtea6-plugin 
```

Eclipse after that should be fairly easy; the eclipse version in the repositories is significantly older than the one from the eclipse website, so  I would install the website version in this case.

---


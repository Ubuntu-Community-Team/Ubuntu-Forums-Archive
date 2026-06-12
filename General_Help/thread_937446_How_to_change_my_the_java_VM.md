---
title: "How to change my the java VM"
date: 2008-10-03
forum: General Help
---

### Post by pedrotuga on 2008-10-03
Lattely I've been facing some problems in some sites that use java applets, for example, poker sites.

I then recall I had installed an implementation of java from the gnu project rather than SUN's.

I like the gnu project and I love to use free (in the whole sense of the word) software, just that this time the restrictions that imposes me are just too restrictive.

So this is the info about my JVM, runtime environment or whatever is the correct term:

> p@p-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Server VM (build 1.6.0_0-b11, mixed mode)
p@p-laptop:~$ 


How do I install SUN's Java?
I assume I need to remove some installed packages (which ones?) and install some others.
Is SUN stuff on the repos or is there any licence incompatibility?

EDIT: Is it possible to keep both implmentations and change the active one whenever I need?

---

### Post by Bakon Jarser on 2008-10-04
It looks like it is in the repos.  If you're dedicated to open source you may want to give IcedTea a shot.  BTW openJDK should be complete by the end of the year.

[http://developers.slashdot.org/article.pl?sid=08/04/23/2037220](http://developers.slashdot.org/article.pl?sid=08/04/23/2037220)

You should be able to just remove openjdk and install IcedTea using synaptic.  It will know if any other packages should be removed.

---

### Post by jespdj on 2008-10-04
To install Sun Java 6:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```
To select which Java runtime environment to use:
```
sudo update-alternatives --config java
```

---


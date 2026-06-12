---
title: "Java applets not working/plugin not present"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by raymund on 2009-02-26
Hi, I've just installed Ubuntu 8.04 in VirtualBox on my Dell/Win XP computer.  My problem is that Java applets aren't working in Firefox.

1. Firefox about: plugins shows no Java plugins.
2. Java is installed: 

```
me@myvirtualcomputer:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
```

3.  icedtea and openjdk are not installed, according to Synaptic.

I'm tempted to completely uninstall Firefox and see if that works.  Any easier fixes you can recommend?

---

### Post by smani on 2009-02-26
In the firefox addressbar, write
```
about:plugins
```
maybe you'll find some useful information there.

---

### Post by Revo___ on 2009-02-26
Possibly there is Java installed but no firefox plugin available.

Try opening a terminal and enter:
```
apt-get update
apt-get install ubuntu-restricted-extras
```

Note:
Those restricted extras also contain the flash player etc.

---

### Post by raymund on 2009-02-26
smani, about: plugins shows nothing Java related.

---

### Post by raymund on 2009-02-26
Revo__, sun-java6-plugin appeared in the list of extras and was set up.  Java plugins appear in about: plugins and the webpages I need it for are working.  Thanks!

Also, here's my Linux newbie question: what's restricted about ubuntu-restricted-extras?

*Nevermind, I saw a description of ubuntu-restricted-extras in the Absolute Beginner's forum.*

---

### Post by jiapei100 on 2012-02-29
Although about: plugins shows nothing related to Java, my Java applet is still working, weird to me...

> **raymund said:**
> smani, about: plugins shows nothing Java related.

---


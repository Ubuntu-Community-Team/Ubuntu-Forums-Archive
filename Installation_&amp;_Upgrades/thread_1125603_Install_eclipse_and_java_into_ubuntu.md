---
title: "Install eclipse and java into ubuntu"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by tamas305 on 2009-04-14
I am a Java programmer and I heard that Ubuntu was very developer friendly so I installed it onto my 8gb usb drive ([full install, with functional windows partition]("http://ubuntuforums.org/showthread.php?t=1116206&highlight=tamas305")). I downloaded the eclipse sdk onto my computer and than used a rather strenuous terminal install to install java runtime environment onto my computer. However when I run eclipse, it gets an error message...

"A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/media/OS/eclipse/jre/bin/java
java in your current PATH"

It says that it search a location at that address however eclipse does not have a jre subfolder, what gives?

Thanks beforehand
-tamas

---

### Post by madmaxo on 2009-04-14
Ubuntu provides eclipse in its repositories and should install all dependencies including java automatically. Are you installing the Ubuntu-provided package? (In Applications -> Add/Remove Software)

---

### Post by Bakon Jarser on 2009-04-14
He probably wants the latest version, not the one in the repos.  Check out this tutorial.

[http://ubuntuforums.org/showthread.php?t=941461&highlight=eclipse](http://ubuntuforums.org/showthread.php?t=941461&highlight=eclipse)

---

### Post by tamas305 on 2009-04-14
I went to eclipse's website and downloaded it from one of the mirror sites, I think it was the first one. However I managed to figure it out, just in case anyone cares (this also works for installing the java plugin for firefox 3).

1) Boot up Ubuntu and open up a terminal (Applications --> Accessories -- > Terminal)

2) Type 

```
sudo su
```

3) Enter your password, you will not see what you enter (a security feature)

4) Type

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

5) Agree to the license agreement and let it install, restart firefox or any other program that needs JAVA and it should work

-tamas

---


---
title: "unable to install program because directions cause errors"
date: 2008-09-10
forum: General Help
---

### Post by jayde_drag0n on 2008-09-10
i am trying to follow the directions posted here [http://ctas.paterva.com/view/Userguide#Linux](http://ctas.paterva.com/view/Userguide#Linux)
to install the program.. when i follow the first direction i get the following error

jayde@MASTER:~/Desktop$ java –jar MaltegoInstaller.jar
Exception in thread "main" java.lang.NoClassDefFoundError: –jar
Caused by: java.lang.ClassNotFoundException: –jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

what do i need to do to resolve the error

here is the version of java i'm using
jayde@MASTER:~/Desktop$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

---

### Post by unca.paka on 2008-09-10
Try installing the Java SDK
```
sudo apt-get install java-sdk
```
will do it I think, if not use Synaptic and search for Java

---

### Post by jayde_drag0n on 2008-09-10
ugh no thats not it.. i just found the problem  first the file i downloaded had a different name because it was a newer version.. fixed that then got the same error... i decided this time to actually TYPE out what i wanted instead of pasting   i noticed the difference..   from the website they had typed --  which looks like just one dash when pasted into terminal!! when i typed it out and put just -jre  it worked fine   bleh.. i hate pebkac errors

---

### Post by unca.paka on 2008-09-10
Well, thats what i get for posting at 4am...glad you got it working though.

---


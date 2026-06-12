---
title: "ArcExplorer Java"
date: 2008-11-26
forum: General Help
---

### Post by dormant on 2008-11-26
I have installed ArcExplorer 9.3 Java as per instructions and am having exactly the same problem as [this poster]("http://ubuntuforums.org/showthread.php?t=486163").

> 
% aejava
Exception in thread "main" java.lang.NoClassDefFoundError: com/esri/ae/AE
Caused by: java.lang.ClassNotFoundException: com.esri.ae.AE
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: com.esri.ae.AE.  Program will exit.


Has anyone got ArcExplorer Java working in Ubuntu?

arcexplorer93_linux
Ubuntu 8.10
sun-java6

---


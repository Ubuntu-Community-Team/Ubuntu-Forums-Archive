---
title: "SunSDK Netbeans error running script"
date: 2008-08-14
forum: General Help
---

### Post by pcjunkie on 2008-08-14
I have installed Netbeans and Sun Java 6 SDK. I attempted to run a java script from a USB drive and I get this output. I am not that experienced at Linux but I know the script works In windows. 

Perhaps I am missing something in setting it all up. Not much instructions on this I am afraid. Plenty for Win...

gamer@gamer-desktop:/media/disk/java$ java TryMath.java
Exception in thread "main" java.lang.NoClassDefFoundError: TryMath/java
Caused by: java.lang.ClassNotFoundException: TryMath.java
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: TryMath.java. Program will exit.

I would really like to learn programming on Linux rather than M$..
Any help of links to correct SunSDK setup and "hooks" would be great.

---


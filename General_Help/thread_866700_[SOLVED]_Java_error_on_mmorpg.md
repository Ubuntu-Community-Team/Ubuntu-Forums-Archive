---
title: "[SOLVED] Java error on mmorpg"
date: 2008-07-22
forum: General Help
---

### Post by dodle on 2008-07-22
I'm getting the following error when trying to start the Wyvern client:> :/games/wyvern$ java client.jar
Exception in thread "main" java.lang.NoClassDefFoundError: client/jar
Caused by: java.lang.ClassNotFoundException: client.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
Any ideas on why I can't get the game to start?

---

### Post by Gunman1982 on 2008-07-22
Try 'java -jar client.jar'

---

### Post by dodle on 2008-07-23
> **Gunman1982 said:**
> Try 'java -jar client.jar'

I get this error:[QUOTE=My Terminal]:/games/wyvern$ java -jar client.jar
Failed to load Main-Class manifest attribute from
client.jar[/QUOTE]

---

### Post by dodle on 2008-07-24
This seems kind of strange to me, but I fixed this by making a launcher for the file called "wyvernclient" in the directory.  What's odd is that it doesn't function if I just try to launch the .py file with python.

---


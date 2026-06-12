---
title: "DrJava + Eclipse in Gutsy issue"
date: 2008-11-11
forum: General Help
---

### Post by vergeh on 2008-11-11
I'm currently using Gutsy, with Eclipse 3.2, and I'm having a serious issue with the DrJava plugin.

I downloaded the v0.9.8 plugin zip for eclipse, and unzipped it in /usr/lib/eclipse/plugins. It created a folder. Permissions were preventing me from unzipping it as anything other than the superuser. 

When I open the DrJava perspective, the window goes gray (sure sign things are not responding), and idles forever. I have to force quit. I've tried making the folder permissions global, and marking the .jar file therein as executable, but this doesn't seem to be fixing the issue.

Has anyone encountered this problem? How do I fix it?

---

### Post by vergeh on 2008-11-13
Bump + update:

thought I'd include the thrown error when Eclipse terminates badly:

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata e000e
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

---


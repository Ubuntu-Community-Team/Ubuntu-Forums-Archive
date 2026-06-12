---
title: "problem while installing eclipse in ubuntu 9.04"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by manan_shah on 2009-07-28
I selected eclipse through the synaptic package manager, and installed it. But when I try to start it, I get the following error. I am not able to interpret the meaning of the error. If somebody can, please tell me what the problem is and what should I do.

The following is the error output:

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/share/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 1e8014
-install /usr/share/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/share/eclipse/startup.jar 

I will be grateful if someone is able to solve the problem for me

---

### Post by Partyboi2 on 2009-07-29
Hi, try this workaround mentioned [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=668438").

---

### Post by feydrutha on 2009-07-29
The version of eclipse in the ubuntu package manager is 3.2. It is several years old, and is much more buggy than the current version 3.5. I was using it myself until a short while ago. 

You can install the 3.5 which is MUCH better very easily from [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/). Just download the 32 or 64-bit linux tarball, unpack it somewhere and run the eclipse binary that is in there. Create yourself a launcher icon and you're done. Just make sure you have a reasonable java virtual machine installed (like openjdk-6-jre or sun-java6-jre).

Also, at that url you find eclipse distros prepackaged for specific purposes, such as the one for C++ development that I am using. Saves you some more time. I am really impressed with the way CDT has been coming along, it's as close to satisfied as I have ever been with an IDE for C++. And the version of CDT in the ubuntu repositories is useless, buggy, and crashy. I have not yet had a single crash of eclipse 3.5.

Don't blame the debian/ubuntu packagers too much: apparently, packaging eclipse is pretty complicated (after all eclipse has its own plugin framework, plus it can run on multiple java vms, etc). And for a developer manual installation should not be a big challenge. But maybe they should just remove it from the repos altoghether since it is so old: i used 3.2 for a long time with considerable pain until i realised how outdated it was.

---

### Post by satysalokhe on 2011-08-23
There are many reasons for this, one of them is,

Please make sure that there are no special characters on your eclipse installation path.

For example : I have extracted eclipse on path "/home/documents/d: drive backup/eclipse/.."

So when I was trying to start eclipse I was getting this error 

When i rename my folder without **":"** its working fine for me.

---


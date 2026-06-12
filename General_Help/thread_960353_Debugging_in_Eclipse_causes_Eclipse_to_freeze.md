---
title: "Debugging in Eclipse causes Eclipse to freeze"
date: 2008-10-27
forum: General Help
---

### Post by Dragros on 2008-10-27
Hey guys, this is one of my first times posting here and I hope I can make it one of my last times posting with a problem...

I am currently in a C++ Programming class and I use Eclipse to do the majority of my work. Lately, when I click the button to start debugging a program I have written a loading bar appears in the bottom-right of my screen that reads "Launching." It will get to 50% then the Eclipse window will go grey and I will have to force quit it. After quitting I am greeted with a rather happy window that says something is up with java. I can't figure out the problem. A prompt reply would be AMAZING! here is a copy/paste of the error window in question.

JVM terminated. Exit code=1
/usr/lib/jvm/java-6-sun/bin/java
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
-exitdata 128020
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

Thanks in advance!
-Dave

---

### Post by Dragros on 2008-10-27
I may have actually found the problem. I just read that openjdk should be installed to run eclipse, but I did not have this. I am installing it now. I will reply if it works.

---

### Post by Dragros on 2008-10-27
that did not fix the problem, but now the error message is slightly different:

JVM terminated. Exit code=1
/usr/lib/jvm/java-6-openjdk/bin/java
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
-exitdata 128020
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-openjdk/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

---

### Post by Dragros on 2008-10-27
also, the debugger sometimes does work but it will quickly scroll through some red text in the console that reads "No source file named Event.cpp" 

Event.cpp was a file used in a previous project but it seems that eclipse is looking for it in my new project.

It also reads in the console "Stopping due to shared library event."

---

### Post by Dragros on 2008-10-27
I figured it out... It was trying to work with all of my projects at once because they were all open. I just closed the old projects and now it works perfectly. Oh well, lots of posts about nothing I guess =D

---


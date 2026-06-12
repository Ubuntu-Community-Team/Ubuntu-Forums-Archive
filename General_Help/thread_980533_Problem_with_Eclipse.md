---
title: "Problem with Eclipse"
date: 2008-11-12
forum: General Help
---

### Post by mojo_man on 2008-11-12
Hello,

I just installed 8.10 on my system

I installed Eclipse to do some java work and whenever I try and execute a program I get the following error:

Exception in thread "main" java.lang.NoClassDefFoundError: Employee
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: Employee not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/mohit/workspace/***#4/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)

--------------

I have tried installing jdk-6.0 but it does not seem to help...

What do I have to get my programs working?

---

### Post by shadanan on 2008-11-12
hi mojo_man,
Even though you have installed jdk-6.0, gcj is still likely the vm that is being used.

Run this at the command line to switch the current vm:

sudo update-alternatives --config java

You will be presented with alternatives that provide java. Type the number corresponding to java-6-sun and try eclipse again.

On a related note, the version of eclipse in the repository is actually two released old. You might want to consider downloading the latest one from the eclipse website.

Regards,
Shad

---

### Post by mojo_man on 2008-11-12
> **shadanan said:**
> hi mojo_man,
Even though you have installed jdk-6.0, gcj is still likely the vm that is being used.

Run this at the command line to switch the current vm:

sudo update-alternatives --config java

You will be presented with alternatives that provide java. Type the number corresponding to java-6-sun and try eclipse again.

On a related note, the version of eclipse in the repository is actually two released old. You might want to consider downloading the latest one from the eclipse website.

Regards,
Shad

I have the following:

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.3
          3    /usr/lib/jvm/java-gcj/jre/bin/java
 +        4    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         5    /usr/lib/jvm/java-6-sun/jre/bin/java


So the sun one is being used....

So now what do? I installed the java 6 after I installed Ecliple. Should I uninstall Eclipe and then reinstall it? THis is frustrating. I know how to program and justc cannot get the SDK to work!

---

### Post by kernelhaxor on 2008-11-12
Now whats happening is, Sun jvm is being used when you type in java into the terminal but Eclipse is still using gcj ..

To configure Eclipse to use the Sun Jre, do:

1. Open Eclipse and then go to Window -> Preferences
2.  On the left panel, click on Java -> Installed JREs
3.  Then click on 'Add' .. To choose the location, click on Browse and then navigate to the location where Sun java is installed.. (for me that was: /usr/lib/jvm/java-6-sun-1.6.0.10)  .. most probably if you installed java from the package manager then that would be the location, try it..

Let me know if still experience problems

---


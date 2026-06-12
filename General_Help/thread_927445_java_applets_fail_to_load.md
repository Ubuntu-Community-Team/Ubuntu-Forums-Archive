---
title: "java applets fail to load"
date: 2008-09-23
forum: General Help
---

### Post by hurtstotalktoyou on 2008-09-23
Hey, everyone.

I'm running Ubuntu Studio 8.04 64-bit, and I have ubuntu-restricted-extras installed.  However, I'm having problems running Java applets (specifically, chat applets).

I have Ubuntu Studio 8.04 32-bit installed on another computer, and the chat applets work just fine.  However, on the 64-bit version, I was asked where to save java cache files (something the applet on the other computer--the one that works--never asked of me).  I chose /tmp.  Now the applet just gives me a "loading" message, but it never loads.

I have re-installed the following through Synaptic:
ubuntu-restricted-extras
java-common
sun-java6-bin
sun-java6-jre

And I have rebooted.  But Firefox refuses to load the chat applets.

What do you all suppose I should do, to try and solve this problem?

Thanks!

---

### Post by ju2wheels on 2008-09-23
There is no 64bit version of Sun Java plugin for Firefox (which is needed to run applets) so OpenJDK is what will kick in and its not compatible with everything.

More on this here:
[http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

---

### Post by hurtstotalktoyou on 2008-09-26
Hmm.  So, is there a workaround for 64-bit systems, or do I need to replace the whole operating system to get it to work?

---

### Post by markharding557 on 2008-09-26
you will need 32 bit for now

---

### Post by ju2wheels on 2008-09-26
Install the Icedtea plugin, it should work for most cases, but as stated before its not 100% compatible with Sun Java 6 but I havent had any major problems with it.

The only way to get full Sun Java 6 plugin working at the moment is to run a 32bit version of Ubuntu.

---


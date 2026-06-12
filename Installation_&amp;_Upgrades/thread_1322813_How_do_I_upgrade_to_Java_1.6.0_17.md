---
title: "How do I upgrade to Java 1.6.0_17?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2009-11-11
I'm currently running Java 1.6.0_16 with Firefox 3 but am experiencing some problems with a particulat banking site, where applets do not run correctly. They tell me that I need to upgrade to Java 1.6.0_17.

I checked the Synaptic repositories and found that 1.6.0_16 is still the current version available.

What's the best way to install 1.6.0_17 as an upgrade?

---

### Post by Mighty_Joe on 2009-11-11
Look [at this post]("http://ubuntuforums.org/showthread.php?t=1314202").  Apparently Ubuntu's moving from Sun JDK to Open JDK, so Sun JDK updates have to be done manually.

---

### Post by gewitty on 2009-11-11
> **Mighty_Joe said:**
> Look [at this post]("http://ubuntuforums.org/showthread.php?t=1314202").  Apparently Ubuntu's moving from Sun JDK to Open JDK, so Sun JDK updates have to be done manually.

Hmmm...

I checked that post. It makes specific mention of the fact that the upgrade described ONLY applies to 9.10, not 8.04. I'm still running 9.04 64 bit (tried to upgrade to 9.10, but had all sorts of problems), so I'm unclear if the instructions provided would work or not.

---

### Post by Mighty_Joe on 2009-11-11
> **gewitty said:**
> It makes specific mention of the fact that the upgrade described ONLY applies to 9.10, not 8.04. 

The way I read it is that the repository for 8.04 will be updated to 1.6.0_17.  Newer Ubuntu versions will not receive the updated Java version.  Your options are to uninstall Sun Java and use OpenJDK/JRE from the repository or install the new Sun Java version manually.

---

### Post by gewitty on 2009-11-11
I successfully ran the upgrade thanks. Unfortunately, it didn't solve my problem with the bank site! They say they don't support Linux, but if it's Java-based, I can't see why the OS should be a problem.

---

### Post by Mighty_Joe on 2009-11-11
There's a couple of things that can go wrong.  First [go here]("www.java.com/en/download/installed.jsp") and make sure that the correct version of the plugin is running.

> if it's Java-based, I can't see why the OS should be a problem. 
Were you able to use the site with an earlier version of Java? Some web sites check the user-agent header to make sure that a client is compatible. That's one reason an app wouldn't work on one OS even though the platform will.

---

### Post by gewitty on 2009-11-11
Now things are getting really confusing.

If I call up the Java Control Panel, it confirms that I have Version 6 update 17 build 1.6.0_17-b04 installed. However, if I go to the Java site link you mentioned and run the check, it tells me that I have 1.6.0_0 installed and that I need to upgrade to Version 6 update 17!

I know that I have 1.6.0_17 installed and that I completely uninstalled 1.6.0_16 first. So why the apparent conflict?

---


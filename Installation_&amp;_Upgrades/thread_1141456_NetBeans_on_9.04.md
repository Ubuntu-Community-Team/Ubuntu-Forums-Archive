---
title: "NetBeans on 9.04"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by subi211 on 2009-04-28
When I upgraded from 8.10, I was pleased to see that NetBeans 6.5 was in the package manager.  However, NetBeans has major issues with OpenJDK (notably the font spacing completely screws up), so I'm trying to reinstall it with Sun's.

Because of the authentication required, I couldn't install sun-java6-jdk through the package manager, so I used apt-get to install it, then NetBeans.  However, now NetBeans won't start.  All I get is silence from the icon, and this from the terminal:

```

root@machine:/usr/bin# ./netbeans
Cannot find java. Please use the --jdkhome switch.
root@machine:/usr/bin# ./netbeans --jdkhome /usr/lib/jvm/java-6-sun-1.6.0.13/
No protocol specified

```

...and Google's not giving me anything useful on it.  I get a similar thing if I install NetBeans from the package manager after installing sun-java6-jdk with apt-get.

Can anyone help?  As it is, the NetBeans build in the package manager is unusable.

---

### Post by subi211 on 2009-04-29
I uninstalled OpenJDK, and using apt-get inistalled sun-java6-jdk (the package manager refused to install it).  Getting NetBeans from the packages manager still screwed up, but running the installer sh with --silent made it work.

So basically, don't use NetBeans with OpenJDK.  ;)

---

### Post by shababhsiddique on 2009-05-11
> **subi211 said:**
> I uninstalled OpenJDK, and using apt-get inistalled sun-java6-jdk (the package manager refused to install it).  Getting NetBeans from the packages manager still screwed up, but running the installer sh with --silent made it work.

So basically, don't use NetBeans with OpenJDK.  ;)

So what have done finally??

Downloaded JDK directly from sun? For doing that removing I don't think openJDK is necessary. I am working on NetBeans without doin it.

---

### Post by kpkeerthi on 2009-05-11
> **subi211 said:**
> 
```

root@machine:/usr/bin# ./netbeans
Cannot find java. Please use the --jdkhome switch.
root@machine:/usr/bin# ./netbeans --jdkhome /usr/lib/jvm/java-6-sun-1.6.0.13/
No protocol specified

```

Wait a minute. You are running netbeans as a root? omg.

---


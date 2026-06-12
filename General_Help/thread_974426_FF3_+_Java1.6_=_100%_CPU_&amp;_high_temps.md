---
title: "FF3 + Java1.6 = 100% CPU &amp; high temps"
date: 2008-11-07
forum: General Help
---

### Post by detroit/zero on 2008-11-07
Can anyone tell me why it is that whenever I visit any kind of site that uses Java (yahoo games, for example) Firefox CPU usage shoots straight to 100%?

I notice in htop that there are no less than 4 java_vm processes running whenever java loads. (I've seen as many as six at one time.) 

In my about: plugins, it lists java 1.6 as the only java, but under it in the details section there is a 3-page list of various things and version numbers going back to 1.2

It doesn't seem to slow my system down any, and even though FF3 shows 100% CPU usage in both conky and htop, RAM usage is as low as would be expected.

I'm using FF 3.03 in Hardy```
**Java(TM) Plug-in 1.6.0_07-b06**

 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.6.0_07   MIME Type Description Suffixes Enabled    application/x-java-vm Java 
Yes   application/x-java-applet Java 
Yes   application/x-java-applet;version=1.1 Java 
Yes   application/x-java-applet;version=1.1.1 Java 
Yes   application/x-java-applet;version=1.1.2 Java 
Yes   application/x-java-applet;version=1.1.3 Java 
Yes   application/x-java-applet;version=1.2 Java 
Yes   application/x-java-applet;version=1.2.1 Java 
Yes   application/x-java-applet;version=1.2.2 Java 
Yes   application/x-java-applet;version=1.3 Java 
Yes   application/x-java-applet;version=1.3.1 Java 
Yes   application/x-java-applet;version=1.4 Java 
Yes   application/x-java-applet;version=1.4.1 Java 
Yes   application/x-java-applet;version=1.4.2 Java 
Yes   application/x-java-applet;version=1.5 Java 
Yes   application/x-java-applet;version=1.6 Java 
Yes   application/x-java-applet;jpi-version=1.6.0_07 Java 
Yes   application/x-java-bean Java 
Yes   application/x-java-bean;version=1.1 Java 
Yes   application/x-java-bean;version=1.1.1 Java 
Yes   application/x-java-bean;version=1.1.2 Java 
Yes   application/x-java-bean;version=1.1.3 Java 
Yes   application/x-java-bean;version=1.2 Java 
Yes   application/x-java-bean;version=1.2.1 Java 
Yes   application/x-java-bean;version=1.2.2 Java 
Yes   application/x-java-bean;version=1.3 Java 
Yes   application/x-java-bean;version=1.3.1 Java 
Yes   application/x-java-bean;version=1.4 Java 
Yes   application/x-java-bean;version=1.4.1 Java 
Yes   application/x-java-bean;version=1.4.2 Java 
Yes   application/x-java-bean;version=1.5 Java 
Yes   application/x-java-bean;version=1.6 Java 
Yes   application/x-java-bean;jpi-version=1.6.0_07 Java 
Yes
```

---

### Post by jamesstansell on 2008-11-07
I don't know about the 100% CPU.  (Especially weird that it doesn't slow your system down!)

One thought - if you install the sun-java6-jdk package you'll have a few more tools for diagnostics, including jps and jvisualvm.

-james.

---

### Post by detroit/zero on 2008-11-07
> **jamesstansell said:**
> I don't know about the 100% CPU.  (Especially weird that it doesn't slow your system down!)Yeah, it's weird. Everything works fine - all my compiz animations/cube, etc.. browsing/copying files.. nothing slows down at all when java is open. > **jamesstansell said:**
> One thought - if you install the sun-java6-jdk package you'll have a few more tools for diagnostics, including jps and jvisualvm.

-james.
I'll give that a try and see what I can learn. Thanks.

---

### Post by detroit/zero on 2008-11-08
After installing the sun-java6-jdk package, whenever I try to load a page that uses java content, my browser freezes and has to be manually killed.

I did manage to check out some of the diagnostic tools that come with that package, though, and they're aimed specifically at developers. I can't even figure out how to use those tools in any meaningful sort of way, much less use the data they give me to fix what's wrong. I don't know how to program in java, and I don't care enough to learn just so I can play yahoo pool.

I don't think I should have to.

---

### Post by ubun_two on 2008-11-08
I am experiencing something similar.  

My system is a quadcore.  Whenever I visit a Java game site, one of the CPU hit 100%, and it doesn't come down.  The whole system doesn't freeze, fortunately...I guess because I have multiple cores.

Looking at the system monitor, it's clearly Java plugin that's taking over the CPU.  When I kill the java process, the CPU is released immediately.

I have Intrepid 64bit with OpenJava 1.6

---

### Post by jamesstansell on 2008-11-08
> **ubun_two said:**
> I am experiencing something similar.  

My system is a quadcore.  Whenever I visit a Java game site, one of the CPU hit 100%, and it doesn't come down.  The whole system doesn't freeze, fortunately...I guess because I have multiple cores.

Looking at the system monitor, it's clearly Java plugin that's taking over the CPU.  When I kill the java process, the CPU is released immediately.

I have Intrepid 64bit with OpenJava 1.6

It's interesting that you're also seeing 100% cpu, because you must be using the icedtea6-plugin 64-bit package.  Either it's a coincidence (meaning that you really are seeing different bugs), or else the bug is neither plugin nor architecture specific.

---

### Post by jamesstansell on 2008-11-08
> In my about: plugins, it lists java 1.6 as the only java, but under it in the details section there is a 3-page list of various things and version numbers going back to 1.2

Some applets will specify a java version to use, and these mime types let the browser know that this plugin should be compatible with the plugin that existed when the applet was installed.

If you think this looks bad, you should see what the ms/windows version looks like!

---

### Post by jamesstansell on 2008-11-09
> **detroit/zero said:**
> After installing the sun-java6-jdk package, whenever I try to load a page that uses java content, my browser freezes and has to be manually killed.

Your browser didn't freeze before installing the sun-java6-jdk package, did it?  If I recall you noticed 100% cpu but said it didn't affect the system.

Does it still freeze if you remove the sun-java6-jdk package?

I'm curious because there is a java 6u10 regression that causes a freeze and may be related.

-james.

---

### Post by detroit/zero on 2008-11-09
> **jamesstansell said:**
> Your browser didn't freeze before installing the sun-java6-jdk package, did it?  If I recall you noticed 100% cpu but said it didn't affect the system.

Does it still freeze if you remove the sun-java6-jdk package?

I'm curious because there is a java 6u10 regression that causes a freeze and may be related.

-james.
I tried removing jdk and the problem was still there, so I did a total purge of all things Java and then reinstalled.

The first time I started FF, everything worked fine - low(er) CPU usage, no high temps, only one java_vm process visible in htop.. at first it seemed like I just had a bad install... The second time I started FF, everything was back to the way it was, meaning: back to square one.

Still, though, java sends firefox to 100% cpu usage as in my screenshot above, but no real effects are noticable as far as how the system functions or anything.

---


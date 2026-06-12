---
title: "[repost from Multimedia &amp; Video] Java Web Start (Sun Java 6) problems"
date: 2008-10-25
forum: General Help
---

### Post by JFDR on 2008-10-25
I posted this under
Multimedia & Video

Maybe this is a better place

[http://ubuntuforums.org/showthread.php?p=6026037#post6026037](http://ubuntuforums.org/showthread.php?p=6026037#post6026037)



Hi !

I had previously installed
[http://www.gokgs.com/download.xhtml](http://www.gokgs.com/download.xhtml)
(an applet for playing the board game GO online)

using Java Web Start

and it was working fine for a while

I just went to play, and got a java error message.

Using Synaptic package manager, I reinstalled everything that came up under a search for Sun Java.

But I kept getting the same error

java.lang.IllegalStateException: DynamicProxyManager: Invalid Proxy Type


Here is the full error msg. I get when trying to reinstall the program using Java Web Start
:

java.lang.IllegalStateException: DynamicProxyManager: Invalid Proxy Type
at com.sun.deploy.net.proxy.DynamicProxyManager.reset (DynamicProxyManager.java:318)
at com.sun.deploy.net.proxy.DeployProxySelector.reset (DeployProxySelector.java:62)
at com.sun.javaws.Main.initializeExecutionEnvironment (Main.java:984)
at com.sun.javaws.Main.continueInSecureThread(Main.ja va:170)
at com.sun.javaws.Main$1.run(Main.java:107)
at java.lang.Thread.run(Thread.java:619)


Any ideas?

Thanks

---

### Post by castudil on 2008-11-20
hi Ubunteros! same problem!

Want to use the examples in java.sun.com in my Ubuntu 8.10.

installed java sun 1.6 package , when I try to launch  java webstart application from firefox i obtain the following error:

java.lang.IllegalStateException: DynamicProxyManager: Invalid Proxy Type
	at com.sun.deploy.net.proxy.DynamicProxyManager.reset(DynamicProxyManager.java:369)
	at com.sun.deploy.net.proxy.DeployProxySelector.reset(DeployProxySelector.java:59)
	at com.sun.javaws.Main.initializeExecutionEnvironment(Main.java:1023)
	at com.sun.javaws.Main.continueInSecureThread(Main.java:179)
	at com.sun.javaws.Main$1.run(Main.java:107)
	at java.lang.Thread.run(Thread.java:619)


can't figure it out ... please, any help will be much appreciated

---

### Post by hohenfelsjoe on 2008-12-21
Same thing happening to me, anyone figure this out?

---

### Post by lgbpinho on 2009-03-31
Same happening here. I played at kgs untill today. NOw not only kgs fails but everything that needs java web starter

---

### Post by castudil on 2009-03-31
for me now Java Web Start is working. When I installed Intrepid from scratch the problem was gone. Really don't remember if I tuned Java in some sort of special way or it was fixed just by installing the new Ubuntu. Anyway, hope this info can help you guys.

---

### Post by lgbpinho on 2009-03-31
well.. that is a solution, but there has to be anotheer way, cuz this one is really drastic. Imagine if i lose my documents here everytime that java gives me something like that

---

### Post by castudil on 2009-04-01
my bet is that the application in charge of executing Java Web Start programs is setted up incorrectly, let's say another program that is able to execute Java web Start apps, but not necessary SUN java web start apps. that was the problem on my machine. 

a solution will be something like changing the default virtual machine for the one offered by SUN... this is not the JRE, but a special program for executing java web start appz... almost sure the name of this program is javaw

---

### Post by lgbpinho on 2009-04-01
Do you guys think it is a permission issue?

---

### Post by weaccept on 2009-06-08
I've added the (probable) cause and workaround to the bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/375194](https://bugs.launchpad.net/ubuntu/+bug/375194)

---


---
title: "Firefox locks up on HP Procurve java web interface"
date: 2008-11-19
forum: General Help
---

### Post by Sgurd on 2008-11-19
I'm on an up-to-date 8.04 desktop.

When I try to use Firefox to access the web interface of our HP ProCurve switches the page loads or partially loads but then locks up.  

The status bar usually says something odd like "Java Applet Bob" or "Java Bail".  I can at times see some of the java applets, but usually they're just blank.

Any thoughts on saving me from using IE in a virtual machine?

SSH to the switches works fine.

Switch firmware is also up-to-date.

Here's some of my Java info:
```
me@ubdesktop:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
me@ubdesktop:~$ which java
/usr/bin/java
```

---

### Post by orn on 2009-01-27
Did you ever figure out how to use the web UI on the Procurve with FF on Ubuntu?

---

### Post by angus73 on 2012-02-22
Well, I am sorry to reply after so long, but the problem still exists for me in the following configuration:

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.10) (6b20-1.9.10-0ubuntu1~10.04.3)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)

Ubuntu Lucid desktop, 64bit

Firefox 10.0.2

Does anyone have some ideas?

Thank you,
Angus73

---


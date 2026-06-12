---
title: "unable to start azureus (after update from hardy to jaunty)"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by rudedcam on 2009-07-24
Vuse (azureus) won't start when i clic on the icon. here are the things i tried without success:
```
sudo apt-get install vuze
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vuze is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
```
sudo update-alternatives --config java
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

```
```
sudo apt-get install sun-java6-jreReading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

can somebody help me out?

---

### Post by Partyboi2 on 2009-07-25
Hi, try starting vuze from the terminal and see if it provides any information.
```
vuze
```

---

### Post by rudedcam on 2009-07-25
```
vuse
bash: vuse: command not found

```
```
azureus
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

```

---

### Post by Partyboi2 on 2009-07-25
> **rudedcam said:**
> ```
vuse
bash: vuse: command not found

``````
azureus
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

```
That was vuze not vuse that was meant to be typed in the terminal. :P You probably can try the workaround mentioned in [[COLOR=Blue]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/348109") bug report.

---

### Post by rudedcam on 2009-07-25
thank you so much partyboi2 it solved my problem :D
YEAH!!! :D

---

### Post by skrap on 2009-07-31
That worked for me too.  Thanks

---


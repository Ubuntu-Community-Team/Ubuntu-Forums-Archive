---
title: "CPU frequency locked to lowest speed"
date: 2008-11-03
forum: Hardware
---

### Post by MacheteMurderer on 2008-11-03
Hi, I'm using Intrepid Ibex and my CPU frequencies have been locked to the lowest available speed.

The governor applet allows me to change the governor mode (powersave, performance etc.) but i cannot actualy increase the clockspeed from 800Mhz to its maximum - or any other higher speed - of 2.2Ghz.

I have done 

$ sudo dpkg-reconfigure gnome-applets

to give the governor applet root privileges but that doesn't seem to be the problem, I've looked into a bug [https://bugs.launchpad.net/ubuntu/+bug/88899](https://bugs.launchpad.net/ubuntu/+bug/88899)
but I'm not convinced the problems are the same yet.

Thanks in advance

---

### Post by notrix on 2010-10-07
Hi,

I have same problem. My laptop can run on 1.9 GHz, but now its stuck on 800 MHz.

Please help.

---

### Post by efflandt on 2010-10-07
Are you sure it is stuck, or could it be that your computer is simply not doing anything cpu intensive.  I have not installed any applets to monitor or control that, but this is one way to see your frequencies from a terminal (i5 650 3.2 GHz):

While idle:
**cat /proc/cpuinfo | grep MHz**
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000
cpu MHz        : 1200.000

While running glxgears with nvidia video (which also runs my gpu full speed):
**cat /proc/cpuinfo | grep MHz**
cpu MHz        : 3201.000
cpu MHz        : 3201.000
cpu MHz        : 3201.000
cpu MHz        : 1600.000

---


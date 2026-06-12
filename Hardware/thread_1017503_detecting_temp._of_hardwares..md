---
title: "detecting temp. of hardwares."
date: 2008-12-21
forum: Hardware
---

### Post by hanbin973 on 2008-12-21
I'm useing K10 arch. CPU. But lm-sensors dosn't detects my CPU.

There is any way for this??

also is there a way to find out the temp of my raedeon graphic card?( I know that nvidia has one)

---

### Post by nick09 on 2008-12-21
Type aticonfig into a terminal. There is a command line in the instructions that you can use to see the temperature of the card in C degrees. 

To use the internal temperatures with a gui:
[http://xibex.blogspot.com/2008/11/monitor-cpu-temperatures-in-ubuntu-with.html](http://xibex.blogspot.com/2008/11/monitor-cpu-temperatures-in-ubuntu-with.html)

An alternative to install is computertemp but it has less features than the applet.
```
sudo apt-get install computertemp
```

---

### Post by hanbin973 on 2008-12-23
My CPU's arch. is K10. So lm-sensors can only detect the hardware.

I'm using cpufreq and cpudyn not powerned. 

I found a patch but I have no idea to make this thing work. 

I need everyones help. :)

---

### Post by hanbin973 on 2008-12-23
I found something here

[http://lists.lm-sensors.org/pipermail/lm-sensors/2008-October/024308.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2008-October/024308.html)

---

### Post by sweetsinse on 2009-01-02
i used one of those same links recently above (the new driver from july, NOT the patch to k8temp) to compile a module for 10h family procs:

[http://ubuntuforums.org/showthread.php?t=1005126#post6476449](http://ubuntuforums.org/showthread.php?t=1005126#post6476449)

i explained how to do it there.

---


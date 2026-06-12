---
title: "How To Measure Performance under Hoary 5.04 ?"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by Shinkan on 2005-04-18
Hi !

I just want to benchmark my PC under Ubuntu Hoary 5.04, it seems to be quite slow compared to Windows (I'm new to the community ! And that won't make me back to Windows, don't worry !).
I want to know how could I test my hardware, and compare it, and/or improve my performance !

I have a SATA 8Mb cache Maxtor DD
ATI Radeon 9800Pro (with fglrx)
P4 HT 3.2 GHz (with -smp kernel)
2 Gb of DDR PC3200
MSI Intel 865Pe Neo2 Platinium

Thx !

---

### Post by TravisNewman on 2005-04-18
hdparm is a good way to improve your hard drive performance. I think it's included by default. If not, you can install it using synaptic. then "man hdparm" to get usage info.

---

### Post by heimo on 2005-04-18
hdparm is a nice quick way to check that you're getting the kind of performance you should, another tool for that purpose is bonnie - with hdparm, chech that DMA is enabled for your CD/DVD drive
 
What hdparm -tT is for hard disks, glxgears is for GPU. It's not a real 3D performance test, but it can give you an idea if everyhing is ok or not.
 
Also consider configuring prelinking (for applications to start faster) [http://www.ubuntuforums.org/showthread.php?t=1971]("http://www.ubuntuforums.org/showthread.php?t=1971")
 
One very basic tool to check what's a bottleneck is top. Run it in terminal and use P to sort processes with CPU usage and m or was it M to sort with memory usage.
 
If the system feels slow, you need to find the bottleneck - chances are that it's a misbehaving / not configured device / feature. Sometimes logs give you good hints (/var/log/messages).
 
Install processor spesific kernel. Check that your X is correctly configured (graphics drivers). Try if there's significant difference between 16 and 24 bit colors (sometimes it's huge).

---

### Post by Shinkan on 2005-04-18
Thanx to everybody !
These answers fit m well !

---


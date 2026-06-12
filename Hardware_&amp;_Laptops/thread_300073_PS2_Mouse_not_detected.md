---
title: "PS/2 Mouse not detected"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by Verminox on 2006-11-15
I just installed Kubuntu on my PC along with WinXP for dual boot. Somehow my PS/2 compatible optical mouse is not being detected by kubuntu at all. I have both Ubuntu and Kubuntu 6.06 LTS Live CDs and it did not get detected on the LiveCD, nor after installation.

The mouse works fine under windows. At start up the mouse light comes on, so i don't think it is a problem with the hardware. Then I reach the screen where I have to choose which OS to load. If I choose windows, all works fine. If I choose Kubuntu, then while loading when the line "Loading hardware drivers..... OK" comes up, the mouse light just goes of and it does not work after KDE loads.

In fact, if I press any of the buttons or scroll the mosue wheel the pointer just moves a bit randomly then again stops responding.

I tried plugging in an old USB mouse and that works fine in both OSes, but I would rather not use it (the buttons are messed up).

So I assumed it is a problem with the mouse drivers but I'm new to linux and don't really know how to solve this problem. Under windows, the PS/2 mouse uses the following driver files:
C:\Windows\system32\DRIVERS\i8042prt.sys
C:\Windows\system32\DRIVERS\mouclass.sys

Any help?

---

### Post by Verminox on 2006-11-15
Ok I tried my best to use the discover program to detect hardware but could not manage to use it. How do i get it to scan for undetected hardware? Is there any way to force it to look at my PS/2 port and report what it found in that port?

---

### Post by ambar on 2007-01-14
I am having the same problem guys ..hope somebody could help us out

---

### Post by Adam Brockett on 2007-02-21
Same problem.
Most current discussion here: [http://ubuntuforums.org/showthread.php?t=354182](http://ubuntuforums.org/showthread.php?t=354182)
Possible fix here:[http://ubuntuforums.org/showthread.php?t=179818](http://ubuntuforums.org/showthread.php?t=179818), but it may require that you actually have it installed, rather than just running off the liveCd.

The problem seems to be restricted to optical PS/2 mice, through not all of them.

---

### Post by vn_raghu on 2007-07-16
Hi Guyz,

I am facing the same problem too ...
I searched the drivers source code where I found a config file
which says type 'Y' if u r using so and so mouse ...

But, i dint make my hands dirty with it ... Also am not sure how to
build the kernel after making changes to config. file ...

Any further info ?

Cheers ...

---


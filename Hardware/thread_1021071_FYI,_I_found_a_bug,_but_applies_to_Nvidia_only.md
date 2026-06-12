---
title: "FYI, I found a bug, but applies to Nvidia only"
date: 2008-12-24
forum: Hardware
---

### Post by RJARRRPCGP on 2008-12-24
If you install nvidia-glx and run ```
xconfig
``` with the ```
sudo
``` command, the following error message will be displayed: 
(or very close in similarity) 

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Device section "Configured Video Device" must have a Driver
line.

-----------------------------------------------------------------


The XOrg configuration file is fine, because X started like nothing bad happened.

---

### Post by Zorael on 2008-12-24
That's **nvidia-xconfig** not keeping with the times. ;3

xorg.conf (the configuration file for X.Org) used to be much more verbose. More recent versions of X rely more on autodetection, so less has to be explicitly defined. That includes the video driver; upon start of X, it'll probe your videocard and divine its make and model, then pick an appropriate *free* driver. Since Nvidia's proprietary blob isn't free, it doesn't get picked automatically, and hence we can use nvidia-xconfig to find the videocard Driver line to replace its value with "nvidia". It isn't there though; when you generate a new xorg.conf - such as is done when installing - it will be practically blank with just a few near-empty sections. So it whines a bit, then does its work grumbling, creating a (new) Driver line.

xorg.conf is still read. nvidia-xconfig just expects it to be fleshier, as that's how they've always been up until recently (Hardy++).

---

### Post by RJARRRPCGP on 2008-12-25
Thanks for the information.

---


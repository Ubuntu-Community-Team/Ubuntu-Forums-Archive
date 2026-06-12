---
title: "X won't start after upgrade to Intrepid Ibex"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2009-03-14
Hi, everybody,

I just upgraded to 8.10 (from 8.04). I got a couple installation errors (concerning mysqld and akonadi, which couldn't be installed because of low disk space), but it didn't look too bad. However, after the final reboot, X didn't start.

I performed an apt-get autoremove in order to free some disk space, and then mysqld and akonadi seemed to get installed, but X still doesn't start.

It complained about a module called type1 that couldn't be found. I commented it out, but it still didn't work.

I tried an xorg.conf.failsafe in the /etc/X11 directory, but still failed.

The problem seems to be in the Intel Driver (it's an aging Acer laptop with the 855GM chipset), since the last lines of Xorg.0.log are:

```
(II) v4l driver for Video4Linux
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile Intel® GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for v4l
(EE) No devices detected.

Fatal server error:
no screens found

```

I've read somewhere that 8.10 detects Intel Graphics automatically, but there must be something wrong?

---

### Post by skamarla on 2009-03-14
I've fixed it myself. For some reason, the i810 driver didn't work. I have edited manually xorg.conf, so the driver is "intel" instead of "i810", and X has started normally.

Not sure if it's the best way to fix it, but it has worked for me.

---

### Post by shakky on 2009-03-14
How did you manage that. I gave up with intrepid and am using Hardy. Every time I tried to upgrade, the xorg issue happened. At what point did you update xorg.conf, 'cause when I opened it to edit it there was nothing in there.In fact, there wasn't even a xorg.conf file

Look forward to hearing from you

---

### Post by skamarla on 2009-03-15
Strange. The installation has never moved xorg.conf, as far as I know. It's still in /etc/X11/xorg.conf.

The relevant logs where you can see which is your particular problem are in /var/log/Xorg*.log. I worked from there.

After fixing the problem, just run "X".

Hope this helps, good luck!

---


---
title: "stuck on checking battery state after upgrade"
date: 2012-10-01
forum: Hardware
---

### Post by louisJ on 2012-10-01
Hi everybody,

My thinkpad t400, running on Ubuntu 12.04, is stuck at boot on "checking battery state" after an interrupted upgrade. I get to see the boot ubuntu logo but then it goes back to black screen with the logs, and displays "checking battery state".

My graphic card is an Intel mobile 4 series (rev 07). I did apt-get update and dist-upgrade from tty1... but it is still stuck. I tried booting with a previous kernel... same thing. When I type startx in the tty1 I get a black screen and the pointer.

Can you help me please?

---

### Post by 2F4U on 2012-10-01
If you can get to tty1, are you then able to access the system log file? It may contain a hint on where it stucks.

---

### Post by louisJ on 2012-10-01
I am too much of a newbie to be able to check in the log files. But indeed I can access them....
what should I do?

---

### Post by 2F4U on 2012-10-01
Are you able to upload the files to the forum, so that maybe others can help analyzing the files?

---

### Post by louisJ on 2012-10-01
Yes, here are all the logs!
Is it safe to share my logs?

---

### Post by louisJ on 2012-10-01
anyone?

---

### Post by louisJ on 2012-10-01
it is really weird, when I list files into /var/logs  the directory "gdm" has weird permissions:
drw-rw---T

what is this??
edit: ok sticky bit I see ;-)

---

### Post by louisJ on 2012-10-01
interesting, I found this in the logs for gdm:

```
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.2.0
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 2.12.0
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.8.99.905, module version = 2.3.0
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.8.99.905, module version = 0.4.2
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(--) using VT number 8

(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading /usr/lib/xorg/modules/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 0.0.2
(EE) open /dev/fb0: No such file or directory
WARNING: All config files need .conf: /etc/modprobe.d/tpm.con, it will be ignored in a future release.
(EE) intel(0): No kernel modesetting driver detected.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

what should I do?

---

### Post by louisJ on 2012-10-02
THe situation has changed, now I can open display at "checking battery state" by loging into tty1 and typing "startx".
I see the desktop files but no desktop environment (no menu, no bars).
How to reestablish gnome3 please?

thanks

hint: I also have this error when trying to launch virtualbox:
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libGL.so.1: cannot open shared object file: No such file or directory

---

### Post by louisJ on 2012-10-02
Please help!

---

### Post by louisJ on 2012-10-09
up

---


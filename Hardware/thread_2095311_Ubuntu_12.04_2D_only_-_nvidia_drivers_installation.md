---
title: "Ubuntu 12.04 2D only - nvidia drivers installation problem"
date: 2012-12-16
forum: Hardware
---

### Post by gigilatrottola on 2012-12-16
Hi all,

I have an HP envy dv6 with geforce GT 630M.
I read lot of threads without finding a solution (x-swat, nvidia drivers from website, nvidia drivers from package manager).

The situation right now is that even if I install the drivers I don't see them in the additional drivers.

Which info do you need to help me?

UPDATE: 
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)
/usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system


**UPDATE 2**
I reinstalled Ubuntu from scratch, installed updates, rebooted and now 3D is working.
May be I messed up the system during previous installation.
I didn't installed the proprietary NVIDIA drivers... before doing that I'll clone the current system...

---


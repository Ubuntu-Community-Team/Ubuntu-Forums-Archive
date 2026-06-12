---
title: "X broken after upgrade to Jaunty, but works with live cd"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by Kezington on 2009-09-13
Hi folks,

After upgrading to Jaunty, I find the Ubuntu bootup screen loads and the progress bar goes to the end, but after that the screen goes mostly black with some garbage near the top. If I boot up using the live cd, it loads fine. 

I've attached the Xorg.0.log files for the live cd and my native installation. The first difference I see is as follows (differences in [COLOR="Red"]red[/COLOR]).
Broken:
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for [COLOR="Red"]7.4.0[/COLOR], module version = 1.0.0

Live CD:
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for [COLOR="Red"]1.6.0[/COLOR], module version = 1.0.0
[COLOR="Red"]	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled[/COLOR]

Anyone know if/how I can resolve this? Not sure if I'm somehow using the wrong libglx.so in my install, and not sure which package libglx.so is part of.

Later on, the native install log file shows:
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.

If anyone can point me in the right direction, I'd really appreciate it!

Thanks,
Kevin

---


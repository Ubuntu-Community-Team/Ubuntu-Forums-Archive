---
title: "OpenGL on Radeon 9100 freezes system"
date: 2005-11-30
forum: General Help
---

### Post by cronholio on 2005-11-30
Thanks to [this guide]("http://ubuntuforums.org/showthread.php?t=24557"), I managed to install ATI drivers for my system. 

fglrxinfo tells me:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000/9100 PRO IGP Series DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)


Now as soon as I run any OpenGL app (like the gears or a 3D screensaver), the system freezes completely after 2 seconds or so. Any hint where I may start troubleshooting? Xorg.0.log or dmesg don't show anything suspicious.

---

### Post by cronholio on 2005-11-30
There is this line in Xorg.0.log:

> (WW) Ignoring request to load module GLcore

Though later it is being loaded:
> (II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2

Does that make any sense? I would really appreciate some help on this.

---


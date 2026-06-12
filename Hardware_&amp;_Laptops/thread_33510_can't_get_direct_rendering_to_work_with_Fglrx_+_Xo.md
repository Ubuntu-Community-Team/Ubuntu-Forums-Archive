---
title: "can't get direct rendering to work with Fglrx + Xorg"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by Sneseglarn on 2005-05-11
I've been scanning the forums, but noone seems to have the same problem i do, so i figured i'd post a cry for help here.

My machine is athlon xp 3000+, ati radeon 9600xt, nforce2 motherboard.

I use Driver "fglrx" in xorg.conf
x works just fine, but no opengl/3d acceleration

glxinfo | grep direct     renders:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

My kernel version is:
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005

From my Xorg.0.log i found these lines that may have some importance?

(WW) Ignoring request to load module GLcore
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No sym
bols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No sym
bols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No sy
mbols found

(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 4.3.99.902, module version = 8.8.25
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset RADEON 9600 PRO (RV360 4152) found

(WW) fglrx(0): board is an unknown third party board, chipset is supported

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


so, is this enough, you want more? 

and most importantly, please dont tell me that i have to recompile the kernel (i've tried 2.6 several times, but just can't seem to get it right, 2.4 is no problem however).

Oh, and btw, i've had this card running accelerated under Debian Sarge with XF86, with ATI's binary drivers.

Any ideas of what to do? Kind Regards / Mark

---

### Post by spartus4 on 2005-05-11
Looks to me like your kernel module isn't loaded in.  Try lsmod in a terminal and see if it is loaded up.  If it isn't try modprobing it in.

---

### Post by Sneseglarn on 2005-05-11
no, that seems to be correct, what is the module called that i am supposed to insert? when i say insmod fglrx it just says it doesn't exist.


Mod: $ lsmod | grep fglrx
fglrx                 237312  0

so the module is loaded, this was not the problem, however, it complains about unmatching versions in kernel and xorg-driver , this seems to be the problem. anyway to fix this?

---


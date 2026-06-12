---
title: "RADEON 9000, Ubuntu 8.04"
date: 2008-11-25
forum: Hardware
---

### Post by Rowlander on 2008-11-25
I'm trying to get ATI drivers running on my RADEON 9000, but having some issues:

> X@X-laptop:~$  sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/8.04
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Generating package: Ubuntu/8.04
Requested package is not supported.
Removing temporary directory: fglrx-install


I've seen a ton of information online about installing drivers for the 9500+ series, but I'm having trouble finding anything useful for my card. I've heard that using xOrg above v7.1 can cause the problem, but I've yet to see a workaround. I'm running 8.04. Any advice?

> X@X-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 8x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2


---

### Post by Rowlander on 2008-11-25
Any ideas? Are there any decent open-source drivers I could use instead?

---


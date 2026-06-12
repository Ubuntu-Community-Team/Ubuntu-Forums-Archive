---
title: "ATI drivers on Edgy... plz help!!!"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by astronafft on 2007-01-12
Hi

I installed Edgy on my Dell Inspiron 9300, and I'm trying to get fglrx working. I built ubuntu debs and installed xorg-fglrx-driver and fglrx-kernel-source, and I used module-assistant to compile fglrx-kernel, but when i reboot and type fglrxinfo it gives me this:

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

drivers are from ATI's web site: ati-driver-installer-8.32.5-x86.x86_64, 2.6.17-10-generic kernel, Radeon mobility x300.

what am i doing wrong???

thanks a lot

sorry for my bad englisch

---

### Post by astronafft on 2007-01-12
Oh and i forgot 1 more thing...

when I change xorg.conf from "ati" to "fglrx" my X won't start giving me Fatal error

---


---
title: "issues with X server compilation on Virtualbox"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by pratikmunot on 2009-09-14
Hello all, I'm in the process of compiling the latest version of XServer, i.e. MPX on my virtualbox whixh has ubuntu  8.04

While doing so, I got this error:

dlopen: /opt/MPX//lib/xorg/modules/drivers/vboxvideo_drv.so: undefined symbol: resVgaShared
(EE) Failed to load /opt/MPX//lib/xorg/modules/drivers/vboxvideo_drv.so
(EE) Failed to load module "vboxvideo" (loader failed, 7)

I also compiled Virtualbox to get the .so driver and did a symb-link to the drivers located in MPX folder. But in vain.

I would be very obliged with any kind of help on this. Thanks.

---


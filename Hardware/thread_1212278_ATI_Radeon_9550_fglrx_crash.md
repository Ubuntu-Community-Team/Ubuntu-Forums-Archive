---
title: "ATI Radeon 9550 fglrx crash"
date: 2009-07-13
forum: Hardware
---

### Post by kcghost on 2009-07-13
I have been setting up a Mythbuntu box which uses Ubuntu 9.04. I am using the latest kernel as of this writing. Since I need tv-out for a mythtv box, I need to use the proprietary drivers for my ATI Radeon 9550 graphics card. But I have encountered several problems that frustrate and confuse me.

The drivers do not show up in "Hardware drivers", but I installed fglrx anyway through the repostitories. Anytime I try this, xorg crashes the computer when it tries to start (garbled graphical screen and the computer is completley unresponsive). This happens even if xorg.conf is using another driver such as vesa or radeon. To get it to work again I have to uninstall fglrx.

I tried installing from ati.com's package. Just running it and trying to install it gives an error, so I built Ubuntu jaunty packages from it and installed those. First the kernel sources then the xorg fglrx driver, then I ran aticonfig --initial. When I reboot, I get "low-graphics mode" and an error saying it couldn't find the driver. Interestingly enough, if I start up "Hardware drivers" from low-graphics mode in this situation it says I have the drivers installed and they are in use.

Any help on thhis issue would be greatly appreciated, Thanks in advance.

---

### Post by angryfirelord on 2009-07-13
Catalyst 9.4 doesn't support that card.

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English")

You'll have to use an older version of Ubuntu if you want 3D support.

---


---
title: "apt segmentation fault after new Jaunty install"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Viranh on 2009-04-25
Shortly after installation, update-manager or apt begins giving me a "segmentation fault" error, then other programs begin to fail to run (e firefox, returning "segmentation fault"). I've tried reinstalling, but this happens shortly afterwards each time. Booting into recovery mode and running fsck and correcting errors helps for a while, but the error comes back after trying to use apt much. this error is documented on launchpad as [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/341402](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/341402). There isn't a permanent fix listed on launchpad. Does anyone have ideas?

---

### Post by str0g on 2009-04-27
you are not alone with this problem I've add half solution to lanchpad

---

### Post by Viranh on 2009-04-27
My last installation stayed stable for god only knows why. I just still had the problems with my wireless that I've mentioned in my other thread, so Jaunty STILL wasn't usable. I imagine that it would have come back if I'd used it for very long though. I couldn't install alot of packages because I couldn't maintain an internet connection.

---

### Post by Viranh on 2009-04-28
Apparently this is related to the kernel version. Documented here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/)
I will try to use an updated kernel and post results. Credits to Str0g for finding this, thanks!

---

### Post by Viranh on 2009-04-30
I upgraded to the 2.6.29.1 kernel from the mainline ppa while still running Intrepid, then upgraded to Jaunty from update manager and chose the new kernel instead of the 2.6.28.11 one that Jaunty came with on boot, and everything has been working fine since.

---


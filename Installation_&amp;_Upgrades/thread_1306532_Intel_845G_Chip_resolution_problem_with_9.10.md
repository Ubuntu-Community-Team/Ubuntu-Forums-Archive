---
title: "Intel 845G Chip resolution problem with 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by robrist on 2009-10-30
just installed 9.10, however the resolution on my screen remains at a dismal 800x600. tryed to install 915resolution package - which is NOT available for 9.10!!
Any solutions?
regards
robrist

---

### Post by suheimi on 2009-10-31
> **robrist said:**
> just installed 9.10, however the resolution on my screen remains at a dismal 800x600. tryed to install 915resolution package - which is NOT available for 9.10!!
Any solutions?
regards
robrist

I had the same problem with Intel motherboard using Intel GMA X4500
But somehow my resolution work nicely. This is what I done:
1. I suspect ubuntu recognized my graphic card as Radeon
2. So, I go to Synaptic Package Manager and search for "xserver", delete most of xserver graphic driver, such as xserver-xorg-video-ati, xserver-xorg-video-radeon, etc
3. install xserver-xorg-video-intel driver
4. restart
5. voilla, it works, it recognize my intel gma x4500

Please noted that ubuntu karmic koala doesnot have /etc/X11/xorg.conf, but you can add it manually.

Have fun!

---


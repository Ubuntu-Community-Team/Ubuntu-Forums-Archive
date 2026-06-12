---
title: "Ubuntu 12.04.3 32-bit (Unity, Raring HWE stack, Nvidia) completely ignores xorg.conf"
date: 2013-10-08
forum: Hardware
---

### Post by jakub-trybowski on 2013-10-08
For starters, I'm using a 7300GT + driver 304.88. I have the "proposed" and "backports" repos disabled.


After playing a Windows Steam game through Wine 1.7.1 (the latest stable version in the Wine PPA) the system stopped using xorg.conf, so even deleting it doesn't change anything and I'm stuck at whatever settings are in the monitords.xml files, from which it now takes display settings. Changing the driver module from "nvidia" to "vesa" causes only some flickering of the Unity launcher and the "nvidia" module loads regardless. Interestingly, though, xorg.conf gets parsed, but then seemingly something overrides it. 

I've already tried a clean reinstallation of the entire X stack (aptitude purge), as well as installation of the default HWE stack ("xserver-xorg-lts-precise), to no avail. Obviously, there's no use in deleting and recreating xorg.conf.

---


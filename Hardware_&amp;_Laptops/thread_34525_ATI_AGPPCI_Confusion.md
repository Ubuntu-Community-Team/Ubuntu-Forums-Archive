---
title: "ATI AGP/PCI Confusion"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by Fascination on 2005-05-15
Just installed Ubuntu AMD64 and its proving to be less than straight forward in the graphical department. I have a Radeon 9200 AGP card (not the best, but it runs UT2k4 fine under Slackware, which was the main thing) but for some reason Ive encountered quite a few problems:

1) Following the various guides out there to set up the drivers for the AMD64 version, it generally results in X failing to run and having to fall back onto the original Xorg.conf.

2) The Device Manager reads the VT8237 PCI Bridge then shows two entries for the ATI Radeon 9200, both seemingly identical aside from one has (secondar) after it, though the Secondary one does have a different pci.device_subclass value. Even though the card itself is AGP, is this PCI bridge likely to the root of the problem?

3) If I leave the xorg as it comes after install, glxgears gives;

```
4972 frames in 5.0 seconds = 994.400 FPS
4979 frames in 5.0 seconds = 995.800 FPS
4956 frames in 5.0 seconds = 991.200 FPS
4962 frames in 5.0 seconds = 992.400 FPS
```

Which should be higher by some degree at least. Glxinfo shows;

```
fasc@balamb:~$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20040929 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.2.1
OpenGL extensions:

```

Any suggestions?

---


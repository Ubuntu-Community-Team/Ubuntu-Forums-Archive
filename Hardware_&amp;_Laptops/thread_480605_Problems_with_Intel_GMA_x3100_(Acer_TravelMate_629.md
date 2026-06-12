---
title: "Problems with Intel GMA x3100 (Acer TravelMate 6292)"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by j4ni on 2007-06-21
I recently bought a new Acer TravelMate 6292 laptop, which comes with the Intel GMA x3100 graphic card. I cant find the right drivers to get the graphics working properly.
I'm assuming the correct driver is the i830, but how to get it working with the Ubuntu Feisty?

xserver-xorg-video-intel version 2:1.9.94-1ubuntu3 with no succes.

I suppose updating x.org would help. Can the xorg-video-intel version 2.0 which comes with the Gutsy be installed in Feisty? Feisty's package listings do not feature this version all tough it should solve my problem...? I tried installing it but there were problems with depencies. [https://launchpad.net/ubuntu/gutsy/+source/xserver-xorg-video-intel](https://launchpad.net/ubuntu/gutsy/+source/xserver-xorg-video-intel)


( [http://en.wikipedia.org/wiki/Intel_graphics_media_accelerator#GMA_X3100](http://en.wikipedia.org/wiki/Intel_graphics_media_accelerator#GMA_X3100) )
"In May 2007, version 2.0 of the driver (xorg-video-intel) was released, which added support for the 965GM chipset. In addition, the 2.0 driver added native video mode programming support for all chipsets from i830 forward. The driver now supports automatic video mode detection and selection, monitor hot plug, dynamic extended and merged desktops and per-monitor screen rotation. These features are built in to the X.Org 7.3 X server release and will eventually be supported across most of the open source X.Org video drivers."

thanks in advance.

---

### Post by j4ni on 2007-06-21
My bad: [http://ubuntuforums.org/showthread.php?t=471557](http://ubuntuforums.org/showthread.php?t=471557)

---


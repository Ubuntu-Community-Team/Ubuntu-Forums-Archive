---
title: "Repace video card"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by peterhocking on 2009-08-16
Hi

I have a PC running Ubuntu 9.04 64 bit version with a nVidia GeForce 5200 card using the nVidia proprietory drivers. I'm going to replace the video card with a nVidia 7600GT.

Before replacing the video card, should I just disable the proprietory driver or is there more I should do first?

TIA

Peter

---

### Post by mhgsys on 2009-08-16
I guess you'll need to reset xorg to default anyway, Or else your screen will be very messy or X will be loaded into safe graphics mode.

You could indeed remove/disable  the drivers, but still you'll have to reset X to default, telling it not to load the wrong (uninstalled) drivers.

To do that; from console or terminal:

sudo dpkg-reconfigure xserver-xorg



Your xorg.conf will now be default again, allowing you to install another videocard an (automatically) make a new xorg.conf for that.

---

### Post by peterhocking on 2009-08-18
> **mhgsys said:**
> I guess you'll need to reset xorg to default anyway, Or else your screen will be very messy or X will be loaded into safe graphics mode.

You could indeed remove/disable  the drivers, but still you'll have to reset X to default, telling it not to load the wrong (uninstalled) drivers.

To do that; from console or terminal:

sudo dpkg-reconfigure xserver-xorg



Your xorg.conf will now be default again, allowing you to install another videocard an (automatically) make a new xorg.conf for that.

Thanks for that, much appreciated.[http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif)

Peter

---


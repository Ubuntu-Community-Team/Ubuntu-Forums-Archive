---
title: "speckles in the screen"
date: 2015-05-01
forum: Hardware
---

### Post by palmgrower on 2015-05-01
Since I installed 15.04 fresh, I am getting speckles on the screen, occasionally, on parts of the screen. Also, the PC freezes once every few hours. Is this a typical graphics issue? My setup is pre-2010.

Intel Q9300 Core 2 Duo
nVidia GT 240
4 GB x2 DDR2

I could not install 14.10 because of graphic issue. I had to install from MinimalCD by line command, and added Unity afterward. With 15.04, installation was ok. But screen breaking up (?). Thanks.

EDIT: No gaming. Speckles and dots appear/disappear on screen even while idling.

---

### Post by v3.xx on 2015-05-02
I say yes, install a proprietary driver using software-sources.  From terminal:
```
software-properties-gtk
```
[http://www.nvidia.com/Download/driverResults.aspx/80533/en-us](http://www.nvidia.com/Download/driverResults.aspx/80533/en-us)

---

### Post by tokyobadger on 2015-05-03
Might be the nvidia/compiz issue - [read this thread](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-346/+bug/1314367)

Your card is new enough for "latest" drivers so trying a ppa like xorg-edgers might be another avenue

---

### Post by palmgrower on 2015-05-03
Thanks for the replies.
As instructed, "software-properties-gtk" was entered in Terminal. A new window popped. In the last tab (Additional Drivers), the first driver (driver 340, tested) was selected. Rebooted PC. Now screen is perfect. No speckles, no freezes. Thanks.

---


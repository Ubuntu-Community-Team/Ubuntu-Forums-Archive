---
title: "Displaylink Help"
date: 2014-03-28
forum: Hardware
---

### Post by Kocrachon on 2014-03-28
Right now I am using 12.04 LTS. I currently am using my onboard video  for one monitor, and I have a displaylink attached for another monitor.  Right now I am getting the green screen that apparently means that the driver accepts the adapter.

However, I am running into an issue where I need to configure the adapter. I found this example config, I tried to use it but it basically broke things.. I really have no idea how to config this, so any help would be appreciated.

Also, here is my car proc/fb

> cat /proc/fb
0 inteldrmfb 
1 udlfb

```
Section "Device"
Identifier      "intel"
driver          "intel"
EndSection
 
Section "Device"
Identifier      "dl1"
driver          "fbdev"
Option  "fbdev" "/dev/fb1"
EndSection
 
Section "Monitor"
Identifier "monitor0"
EndSection
 
Section "Monitor"
Identifier "monitor1"
EndSection
 
Section "Screen"
Identifier "screen0"
Device "dl1"
Monitor "monitor0"
DefaultDepth 16
EndSection
 
Section "Screen"
Identifier "screen1"
Device "intel"
Monitor "monitor1"
DefaultDepth 16
EndSection
 
Section "ServerLayout"
Identifier     "multihead"
Screen      0  "screen0" 1280 0
Screen      1  "screen1" LeftOf "screen0"
Option    "Xinerama" "on"
EndSection



```

---

### Post by Kocrachon on 2014-03-28
Here are the results of my grep for the drivers.

grep -i drivers /var/log/Xorg.0.log 
[    22.399] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so 
[    22.466] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so 
[    22.491] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.498] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so 
[    22.509] (II) modesetting: Driver for Modesetting Kernel Drivers: kms

Right now I have got it sort of working, but the graphics are messed up and look very werird. If I try to enter the display option it tells me it cant, so I think I still hve something configured wrong...

---


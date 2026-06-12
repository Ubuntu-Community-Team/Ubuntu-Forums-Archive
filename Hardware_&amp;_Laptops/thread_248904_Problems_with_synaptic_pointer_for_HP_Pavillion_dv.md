---
title: "Problems with synaptic pointer for HP Pavillion dv6000 - click'n drag errors&quot;"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by martinrandau on 2006-09-01
I have a very annoying touchpad error for my laptop. 

I can only by clicking very hard or trying many times resize or move windows or mark an area on the desktop. Also, marking texts in gedit or here for example hardly works. This leads one to think that it's a clicking error, BUT clicking and pointing in the gnome menu works perfect! Basically, click'n drag doesn't work. 

It's not a hardware error because it worked perfect under Suse 10.1. If I hadn't erased that OS I could have checked in xorg.conf, but it's gone.

Any help is appreciated. Perhaps by posing the relevant section of xorg.conf if you believe that you have a similar model (see title).

Thanks!

---

### Post by mssever on 2006-09-01
Here's my xorg.conf--though you might not like my settings :) (I have an HP Compaq nx9010):
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
        Option          "LockedDrags"           "true"
        Option          "PalmDetect"            "true"
        Option          "RightEdge"             "5900"
        Option          "EdgeMotionMinSpeed"    "0"
        Option          "EdgeMotionMaxSpeed"    "0"
EndSection
``` Typing man synaptics will give you complete documentation on the settings available and what they do.

---

### Post by martinrandau on 2006-09-01
Thanks for the try, but it doesn't change anything. It's very odd.

It seems as if the problem has nothing to do with X but maybe with some drivers or hardware configuration that goes beyond my knowledge. :(

---


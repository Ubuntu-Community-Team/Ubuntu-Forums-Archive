---
title: "3d video driver for Radeon IGP 340M"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by merinda on 2005-11-03
I have VGA compatible controller: ATI Technologies Inc Radeon IGP 340M. This is my vga section of xorg.conf:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
        Driver          "radeon"
        BusID           "PCI:1:5:0"
        Option          "AGPMode"   "4"
        Option          "AGPMode"   "true"
        Option          "EnablePageFlip"   "true"
EndSection

But I still can't play ppracer ( 3d game ) without lag. Any help? Thank you. I have tried fglrx driver but my laptop does not support this driver.

---

### Post by jecos on 2005-11-03
Get rid of "AGPMode" "True" and put "AGPFastWrite" "True".  I also have driconf installed to modify graphic settings --> [http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)

---

### Post by merinda on 2005-11-04
Done that. No good. Any idea?

---

### Post by jfryman on 2005-11-04
Unfortunately, the Radeon IGP320/340M are not fully 3d enabled at this point. There are a series of howto's that you can follow to enable DRI on your laptop, but these are emulated through Mesa, which use your CPU to do rendering. If you're still interested, check out:

[http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=179](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=179)

It's something that I've been trying to come to terms now for about a year and a half. :) 

Either way, good luck!

---


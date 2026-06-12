---
title: "mouse serial on hoary"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by sabitha on 2006-06-11
i cant get my serial mouse to work even i edit my xorg.cong and replace the mouse with this :

Section "InputDevice" 
        Identifier      "Configured Mouse" 
        Driver          "mouse" 
        Option          "Device"                "/dev/ttyS0" 
        Option          "Protocol"              "Microsoft" 
EndSection

---


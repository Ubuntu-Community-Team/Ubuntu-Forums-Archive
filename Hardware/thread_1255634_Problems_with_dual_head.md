---
title: "Problems with dual head"
date: 2009-09-01
forum: Hardware
---

### Post by Carbie on 2009-09-01
Hi:
    I am learning Cadence now. If I can have dual head with my OS, that would be easy for the design. But no matter how I modify the xorg.conf file according to the google, the head won't work. Instead, they turn out to be black. This issue troubles me a lot. Can anyone help me deal with it?
   BTW, my hardware configuration: Intel 82865G vedio card with DVI and VGA interfaces. I suppose each interface connecting with one head.

---

### Post by newton21989 on 2009-09-03
Does xrandr see multiple interfaces? If so, you can use it to set up the monitors as you like. You may have to add a "Virtual" parameter the the "Display" subsection in xorg.conf at least the size of both monitors combined. I have a 1440x900 next to a 1280x1024. Mine looks like this:
```

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Laptop Panel"
    Device        "Laptop Panel Device"
    SubSection "Display"
        Depth    24
***        Virtual    2720 1024***
    EndSubSection
EndSection

```

---


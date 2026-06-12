---
title: "Fujitsu P7010 widescreen support on Dapper"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by melon on 2006-05-28
Hi folks,

I just installed Xubuntu on my Fujitsu P7010. It has Intel 855 integrated VGA, and a native 1280x768 widescreen display. On 5.10, I used a tiny util called [855resolution]("http://perso.wanadoo.fr/apoirier/"), but that doesn't compile on Dapper. I would like to use my screen at 1280 wide but only 1024 is supported by default.

relevant info from my xorg.conf:
```
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
...
        SubSection "Display"
                Depth           24
                Modes           "1280x768"
        EndSubSection

```

Anyone?

---

### Post by melon on 2006-05-29
Gee, I was in write-only mode, sorry. Installing 915resolution and restarting X worked like a charm. I wonder why doesn't it install itself by default?:confused:

---


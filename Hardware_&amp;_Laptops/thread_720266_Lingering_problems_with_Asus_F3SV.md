---
title: "Lingering problems with Asus F3SV"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by ksadil on 2008-03-10
Hello,

Screen Resolution - X starts in 1600x1024 instead of the maximum 1680x1050. even though my xorg.con specifies the higher resolution.

.
.
.
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection........




Wireless Lan also  drops out - reboot required to reestablish, normally get 3 hours, but overnight nearly always drops out.


Also "suspend" is not friendly - especially if suspended for a few hours. Sometimes the screen never wakes up even though it is obvious that the system has( hard disk & dvd drive all makes start up sounds. 


Any ideas or assistance appreciated.

Thanks,
Kim

---


---
title: "Dell D630 Dual Monitor Question"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by henry95 on 2007-11-09
I'm trying to add another monitor to my dell D630 laptop.  It has an intel graphics card.  My other monitor is a Dell 1907FP.

It works if I use Fn F8, and mirrors my display, what I want is it to extend my laptop screen to the right.

Can anyone help me out?

-Cheers

---

### Post by tpearson@alltel.net on 2007-11-09
here's part of my config, works well.   twinview is the main piece you need.

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1905FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---


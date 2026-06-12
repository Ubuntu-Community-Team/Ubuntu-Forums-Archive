---
title: "Xorg"
date: 2012-12-02
forum: Hardware
---

### Post by Tysonv48 on 2012-12-02
Hi im seeking support with creating a xorg.conf file. I am using an eee pc 701 laptop with an intel 910gml chipset.

What i want is to be outputting 640x480i @ 30Hz (15khz) so that the screen in my car can accept the video.

So far i have been unable to add the above resolution in xrandr using modelines that i generate in cvt or gtf. Using xorg i have been able to add 480i as a resolution in LVDS but not VGA. 

so in short i need help with making a xorg file to set the VGA output to 640x480i through a screen with no edid or vendor information.

[EDIT] Forgot to add I'm using Ubuntu 8.10

Here is my current Xorg.conf

Section    "Files"
    ModulePath    "/usr/lib/xorg/modules"
EndSection

Section    "Module"
    Load    "glx"
    Load    "dri"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "ASUS"
    ModelName    "eeePC P701"
    Modeline     "800x480"  29.58  800 816 896 992  480 481 484 497  -HSync +Vsync # 60 Hz
    Modeline     "640x480"  11.75  640 664 720 800  480 483 487 492 -hsync +vsync interlace
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    Modeline     "644x483"  11.75  648 672 728 808  483 486 496 499 -hsync +vsync # 30 Hz
EndSection

Section "Monitor"
    Identifier    "External"
    VendorName    "FUS"
    HorizSync    15
    VertRefresh    30
    Option        "DPMS"
    Option        "PreferredMode" "640x480"
EndSection



Section "Monitor"
    Identifier   "TV"
    VendorName   "ASUS"
    ModelName    "eeePC P701"
    Option       "Ignore" "true"
EndSection

Section "Device"
    Identifier  "Device1"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
    BusID       "PCI:0:2:0"
    Option      "Monitor-VGA"  "Monitor1"
    Option      "Monitor-LVDS" "Monitor1"
    Option      "Monitor-TV"   "TV"
    Option      "XAANoOffScreenPixmaps" "true"
    Option      "AccelMethod" "XAA"
    Option      "UseEDID" "False"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Device1"
    DefaultDepth     16
    SubSection "Display"
        Depth     8
        Virtual  1024 768
    EndSubSection
    SubSection "Display"
        Depth     15
        Virtual  1024 768
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes     "640x480@30" "640x480_30"
    EndSubSection
    SubSection "Display"
        Depth     24
        Virtual  640 480
    EndSubSection
EndSection


Section "Device"
    Identifier  "Device2"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
    BusID       "PCI:0:2:1"
    Option      "Monitor-VGA"  "Monitor2"
    Option      "Monitor-LVDS" "Monitor1"
    Option      "Monitor-TV"   "TV"
    Option      "XAANoOffScreenPixmaps" "true"
    Option      "AccelMethod" "XAA"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Device2"
    DefaultDepth     16
    Subsection "Display"
        Depth    16
        Modes    "644x483" "640x480"
    EndSubSection
EndSection



Section "DRI"
    Mode         0666
EndSection

Section "Extensions"
    Option        "Composite" "Disable"
EndSection

---

### Post by Tysonv48 on 2012-12-04
Easier Question this time

Is it better to use cvt or gtf as they give out different values

---

### Post by philinux on 2012-12-04
Duplicate thread removed.

Is there any reason for running such an old version of ubuntu.

---

### Post by Grenage on 2012-12-04
> **Tysonv48 said:**
> Easier Question this time

Is it better to use cvt or gtf as they give out different values

gtf generates industry-standard timings, and cvt generates VESA-standard timings.  I generally use cvt.

---

### Post by Tysonv48 on 2012-12-04
> **philinux said:**
> Duplicate thread removed.

Is there any reason for running such an old version of ubuntu.

Couldnt install 12.04 due to lack of pae support on the CPU. I have other linux distros but there all 64 bit.

Any recommendations?

---


---
title: "GPU Scaling with Geforce 9600 GSO"
date: 2009-01-27
forum: Hardware
---

### Post by duffrecords on 2009-01-27
I'm using an Olevia LT26HVE TV for a monitor with an NVIDIA GeForce 9600 GSO.  Under normal circumstances, the highest widescreen resolution I can set is 1280x768.  However, I just noticed the GPU Scaling option in nvidia-settings, which should be able to scale a higher display mode to the TV's native resolution.  I added some new modes such as "1440x900" to xorg.conf but after restarting X they don't appear in the list of resolutions in either nvidia-settings or gnome-display-properties, and X simply defaults to 1280x768.  How can I force X to acknowledge the modes I added to xorg.conf?  Here are the relevant sections of xorg.conf:```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DMI LCD Multi-Media Display"
    HorizSync       31.5 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GSO"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x900" "1280x768" "1024x768"
    EndSubSection
EndSection
```

---

### Post by duffrecords on 2009-05-01
bump

---


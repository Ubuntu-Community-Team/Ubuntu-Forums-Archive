---
title: "Twinview with gutsy and NVIDIA"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by regindk on 2007-09-14
I'm trying to get TwinView to work with my T61 IBM LENOVO laptop ( NVIDIA Quadro NVS 140M ) running Gutsy Gibbon tribe 5.

I got the NVIDIA-glx driver installed and have been using the nvidia-settings application to setup the twinview. Following two problems have arisen doing that:

1. Having pluggedin the external monitor after start up and then using nvidia-settings to enable twinview results in two blacked out screens.

2. On start up after using nvidia-settings with the external monitor pluggedin from start, the external monitor works but the laptop-monitor show somekinda graphic that keeps changing the colors. if I then use the nvidia-settings and reposition one of the two monitors the twinview works.

Any ideas on how to enable the twinview without having the external monitor enabled from start?

Any ideas on how to get the twinview to work (without repositioning the screens in nvidia-settings) when the external monitor is plugged in from start?

Related parts from my xorg.conf file:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

...............STRIPPED OUT.........

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: 1680x1050 +0+0, CRT: 1280x1024_60 +1680+0"
# Removed Option "metamodes" "CRT: 1280x1024_60 +1680+0, DFP: 1680x1050 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024_60 +1680+26, DFP: 1680x1050 +0+0"
EndSection

```

---


---
title: "fourth monitor"
date: 2012-05-17
forum: Hardware
---

### Post by handheld-penguin on 2012-05-17
I have three monitors running fine under kde and x11 however I want to add a fourth.

I have two on my discrete gpu and two on my integrated gpu. The two on the integrated gpu are cloning at the resolution of the lowest of the pair :( I want them to extend my desktop, one monitor is 1280x1024 and the other is 1920x1080. The two on the discrete gpu work like a charm.

I've been reading this guide on how to set them up on the integrated gpu ([http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)) but I can't seem to get it going. When I look in the log Xorg tells me that it is ignoring all the options I add.

This is the setup I'm using fwiw...is there anything obvious I am missing to get intel x11 dual monitor extended desktop functionality working with my i7-2600. Works fine in windows.

Jam
Section "Module"
        Load "dri"
        Load "dbe"
        Load "extmod"
        Load "type1"
        Load "freetype"
        Load "glx"
EndSection

Section "Monitor"
        Identifier     "Monitor2"
        VendorName     "Unknown"
        ModelName      "Samsung SyncMaster"
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 60.0
        Option         "DPMS"
EndSection

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Dell 197FP"
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 60.0
        Option         "DPMS"
EndSection

Section "Monitor"
        Identifier     "Monitor1"
        Option "RightOf" "Monitor3"
        VendorName     "Unknown"
        ModelName    "Dell96FP"                                                                                                                                                                                                                         HorizSync       30.0 - 81.0                                                                                                                                                                                                                 
        VertRefresh     56.0 - 60.0
        Option         "DPMS"
        Option "PreferredMode"  "1280x1024"
EndSection

Section "Monitor"
        Identifier     "Monitor3"
        VendorName     "Unknown"
        ModelName      "Acer"
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 60.0
        Option         "DPMS"
        Option "PreferredMode"  "1920x1080"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option         "metamodes" "DFP: nvidia-auto-select +0+0"
        Option         "DisableGLXRootClipping" "True"
        Option         "AllowGLXWithComposite" "True"
        Option         "RenderAccel" "True"
        Option         "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth       24
                Modes      "1920x1080"
        EndSubSection
EndSection

Section "Screen"
        Identifier     "Screen1"
        Device         "Device1"
        Monitor        "Monitor1"
        DefaultDepth    24
        Option         "metamodes" "DFP: nvidia-auto-select +0+0"
        Option         "DisableGLXRootClipping" "True"
        Option         "AllowGLXWithComposite" "True"
        Option         "RenderAccel" "True"
        Option         "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth       24
                Modes      "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier     "Screen2"
        Device         "Device2"
        Monitor        "Monitor2"
        DefaultDepth    24
        Option         "metamodes" "DFP: nvidia-auto-select +0+0"
        Option         "DisableGLXRootClipping" "True"
       Option         "AllowGLXWithComposite" "True"
       Option         "RenderAccel" "True"
        Option         "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth       24
                Modes      "1280x1024" "1920x1080"
        EndSubSection
EndSection


Section "Screen"
        Identifier     "Screen3"
        Device         "Device2"
        Monitor        "Monitor3"
        DefaultDepth    24
        Option         "metamodes" "DFP: nvidia-auto-select +0+0"
        Option         "DisableGLXRootClipping" "True"
        Option         "AllowGLXWithComposite" "True"
        Option         "RenderAccel" "True"
        Option         "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth       24
                Modes      "1920x1080"
        EndSubSection
EndSection

Section "Extensions"
        Option         "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" LeftOf "Screen0"
        Screen     2  "Screen2" RightOf "Screen0"
        Screen     3  "Screen3" RightOf "Screen2"
EndSection

Section "Device"
        Identifier     "Device0"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce GTX 560"
        BusID          "PCI:1:0:0"
        Screen          0
        Option  "NoLogo"        "True"
EndSection

Section "Device"
        Identifier     "Device1"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce GTX 560"
        BusID          "PCI:1:0:0"
        Screen          1
        Option  "NoLogo"        "True"
EndSection

Section "Device"
        Identifier     "Device2"
        Driver         "intel"
        VendorName     "Intel Corporation"
        BoardName      "Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller"
        BusID          "PCI:00:02:0"
        Option  "NoLogo"        "True"
       Option "monitor-TMDS-1" "Monitor3"
        Option "monitor-VGA" "Monitor1"
        Screen 2
EndSection


Section "ServerFlags"
        Option         "Xinerama" "1"
EndSection

---


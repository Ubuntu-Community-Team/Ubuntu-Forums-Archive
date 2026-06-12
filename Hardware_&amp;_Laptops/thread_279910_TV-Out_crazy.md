---
title: "TV-Out crazy"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by kekojeep on 2006-10-18
Hi people.. I'm trying to set up the tv-out on my Geforce Go MX 440 but I'm having some problems.. 

I got my xorg.conf accordingly to a post from someone I can't remember.. I tried both the TV-Out for newbies thread and TwinView thread but none of the two tutorials worked, couldn't even get image on the TV..

Now I have got image displaying on my TV, but everytime I boot with this xorg configuration, there is image ONLY in the TV, and my laptop monitor stays blank.. if I try to log out, screen goes crazy with lots of artifacts, and i have to reboot..

What I'm doing for now to use the tv-out is this (I use this laptop for AutoCAD teaching on a projector, that's why I need the tv-out): I keep two copies of my xorg.conf in a safe folder, so when I'm at home I copy the "original" xorg.conf to /etc/X11 so I can use it displaying normally on the laptop's LCD... When I'm at the classroom for using the projector, I copy the "tv-out configured" xorg.conf to /etc/X11 and boot the computer with that, so it starts up showing everything since the login window on the tv-out.. and so on..

I would really like to fix this problem, if anyone can help, here is my xorg files. I copied only the part about Nvidia's configuration.

Thanks in advance,

André Tomasi


**This is the xorg.conf that works with tv-out but displays nothing in my laptop LCD display..**
```
Section "Device"
    Identifier    "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
    Option        "Coolbits" "1"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Monitor        "Generic Monitor"
        Option          "NoLogo"
        Option          "RenderAccel" "true"
        Option          "TripleBuffer" "true"
        Option        "NvAgp"     "1"
    Option     "TwinView" "TRUE"
    Option     "TwinViewOrientation" "Clone"
    #Option     "HorizSync" "CRT-0: 30-85; TV-0: 31-50" 
    #Option     "VertRefresh" "CRT-0: 50-160; TV-0: 60"
    Option      "SecondMonitorHorizSync" "30-50"
    Option      "SecondMonitorVertRefresh" "60"
    Option     "MetaModes" "1024x768,1024x768"
    Option     "TVStandard" "PAL-M"
    Option "TVOutFormat" "SVIDEO"
    Option "ConnectedMonitor" "TV-0, CRT-0"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

#Section "DRI"
#    Mode    0666
#EndSection

#Section "Extensions"
#    Option "Composite" "Enable"
#EndSection
```**And this is the original xorg.conf that I use with XGL, displaying normally on the LCD.**

```
Section "Device"
    Identifier    "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
    Option        "Coolbits" "1"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Monitor        "Generic Monitor"
        Option          "NoLogo"
        Option          "RenderAccel" "true"
        Option          "TripleBuffer" "true"
        Option        "NvAgp"     "1"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

#Section "DRI"
#    Mode    0666
#EndSection

#Section "Extensions"
#    Option "Composite" "Enable"
#EndSection

```

---


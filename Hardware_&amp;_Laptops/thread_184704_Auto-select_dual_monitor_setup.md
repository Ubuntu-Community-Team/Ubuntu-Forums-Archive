---
title: "Auto-select dual monitor setup?"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by jgoguen on 2006-05-30
I've got an xorg.conf (relevant sections below) that allows me to use an external monitor with my laptop.  It's set up so that the laptop screen is the main screen and the external monitor is to the right, both at 1024x768 (max resolution of the laptop screen.  This works perfectly fine, but what I'm looking to do now is to have a single or dual monitor configuration automatically selected depending on whether there's an external monitor connected or not.  Even if this only happens when the laptop boots, or if I have to restart X after attaching/removing the monitor, that would be fine.  It's very rare that I add/remove a monitor in the middle of a session.  I use the i810 driver.  Anyone know how I could do this?

But if I can can attach/remove a monitor in the middle of a session and resize the desktop without restarting anything, even better :)


xorg.conf:
```
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        0 "Default Screen"
    Screen        1 "Default Screen 2" RightOf "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "ServerFlags"
    Option        "Xinerama"    "True"
EndSection

ection "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "record"
    Load    "type1"
    Load    "vbe"
EndSection

Section "Device"
    Identifier    "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Option        "MonitorLayout"        "CRT,LFP"
    VideoRam    65536
    Option        "FlipPrimary"        "false"
    Option        "DevicePresence"    "true"
    Option        "VBERestore"        "false"
    Screen        0    

EndSection

Section "Device"
    Identifier    "Intel Corporation 82830 CGC [Chipset Graphics Controller] 2"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Option        "MonitorLayout"        "CRT,LFP"
    Option        "DevicePresence"    "true"
    VideoRam    65536
    Option        "VBERestore"        "false"
    Screen        1    
EndSection

#TFT
Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-49
    VertRefresh    43-72
EndSection

#External LCD
Section "Monitor"
    Identifier    "Generic Monitor 2"
    Option        "DPMS"
    HorizSync    28-49
    VertRefresh    43-72
EndSection

Section "Screen"
    Identifier    "Default Screen 2"
    Device        "Intel Corporation 82830 CGC [Chipset Graphics Controller] 2"
    Monitor        "Generic Monitor 2"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection

Section "DRI"
    Mode    0666    #Disable by Xinerama
EndSection
```

---

### Post by RenaudRichardet on 2006-08-08
see "Automatic discovery of docked and undocked status" in [http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/](http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/), it worked for me; Here's the script: [http://rdo.homelinux.org/~will/d610/amidocked](http://rdo.homelinux.org/~will/d610/amidocked)
HTH,
Renaud

---


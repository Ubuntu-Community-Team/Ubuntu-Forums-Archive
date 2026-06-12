---
title: "GDM+Virtual Desktop+9.04-&gt;9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by czester21 on 2009-10-30
hello,

I have a problem with GDM. On ubuntu 9.04 everithing was working great, but after upgrading to 9.10 my gdm login screen have size of my virtual desktop, and I can't even see whole login box, I have to scroll horizontally screen using my mouse to see whole box.

Here is my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout"
    Screen      0  "LCD_SCREEN" 0 0
    Screen      1  "TV_SCREEN"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "off"
    Option         "Clone" "off"
EndSection

Section "Monitor"
    Identifier     "LCD"
    ModelName      "Gateway HD1900"
EndSection

Section "Monitor"
    Identifier     "TV"
    VendorName     "SAMSUNG LE32A551"
EndSection

Section "Device"
    Identifier     "0 NVIDIA GeForce 8600 GT"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
    Option "TwinView" "true"
EndSection

Section "Device"
    Identifier     "1 NVIDIA GeForce 8600 GT"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
    Option "TwinView" "true"
EndSection

Section "Screen"
    Identifier     "LCD_SCREEN"
    Device         "0 NVIDIA GeForce 8600 GT"
    Monitor        "LCD"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option "metamodes" "CRT: NULL, DFP: 1440x900 +0+0; CRT: 1360x768_60_0 +1440+0, DFP: 1440x900 +0+0"
    Option "DynamicTwinView" "true"
    SubSection     "Display"
        Depth       24
        Modes       "1440x900"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "TV_SCREEN"
    Device         "1 NVIDIA GeForce 8600 GT"
    Monitor        "TV"
    DefaultDepth    24
    Option "DynamicTwinView" "true"
    SubSection     "Display"
        Depth       24
        Modes       "1360x768_60_0"
    EndSubSection
EndSection

```On xorg.conf i have two screens, one is my monitor, the other one is my TV. My video card is Nvidia GeForce 8600 GT. I'm using xrandr to switch between displays:
xrandr -s 0 to activate only LCD
xrandr -s 1 to activate LCD with main desktop and TV on the right of my desktop, so for example I can move mplayer window to TV

Interesting thing is that after I log in to the system it's back to normal - LCD is turned on and TV is turned off. The problem is only with GDM - LCD is turned on, it has resolution 1440x900 but the virtual desktop is on so it makes virtual resolution 2800x900 - so it seems that when gdm i starting it's trying to show the whole virtual screen on my lcd, while after log in xorg is showing only 1440x900 of whole 2800x900 virtual screen and the rest is destined to be handled by tv...


EDIT: I've manage to solve the problem, if you can call this solution, a solution:
Because gdm now always chooses first of defined metamode, instead of writing:
```

Option "metamodes" "CRT: NULL, DFP: 1440x900 +0+0; CRT: 1360x768_60_0 +1440+0, DFP: 1440x90

```I'm writing:
```

Option "metamodes" "CRT: 1360x768_60_0 +1440+0, DFP: 1440x900 +0+0; CRT: NULL, DFP: 1440x900 +0+0;"

```In that way my virtaul screen resolution is 2800x900 as it was before, but now TV is ON when gdm starts, so I see log in box on center of my LCD screen, after I log in TV becomes OFF, and I can turn it on or off using xrandr.

---


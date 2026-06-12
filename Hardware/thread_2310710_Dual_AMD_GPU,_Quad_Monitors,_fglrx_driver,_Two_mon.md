---
title: "Dual AMD GPU, Quad Monitors, fglrx driver, Two monitors show black X mouse cursor"
date: 2016-01-21
forum: Hardware
---

### Post by jostein2 on 2016-01-21
Hi 
I'm setting up my new homeoffice with some extra screens, here the issue:
OS: Ubuntu 15.10 x64
 
I have four monitors, two are connnected to a Radeon 7970 and two are connected to a Radeon 5800

[I] fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon R9 200 / HD 7900 Series
OpenGL version string: 4.5.13399 Compatibility Profile Context 15.201.1151

display: :0  screen: 1
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 5800 Series
OpenGL version string: 4.5.13399 Compatibility Profile Context 15.201.1151[/I]

When using open source drivers it will only detect the first GPU use those monitors. 
So I installed the proprietary AMD drivers 
With the proprietary drivers installed I was able to enable the second GPU with amdccle.
So this is what I ended up with in amdccle:

[IMG]http://s15.postimg.org/4khh8n2uj/Selection_001.png[/IMG]


I'm able to move the mouse cursor over the the two upper screens, however with a X as a mouse cursor, also when I start amdccle I do get the screen number, see below:
(The two working screens are connected to the primary card (Radeon 7970))

[IMG]http://s12.postimg.org/vrb4qdgjx/IMG_20160121_104023.jpg[/IMG]

I guess the issue is that X does not use the upper screen or something like that
I started poking around in my xorg.conf, but to be honest it does not make me that much wiser :)

Here's my xorg.conf 

[I]Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 1080
    Screen         "aticonfig-Screen[1]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP10"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP11"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP4"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP10" "0-DFP10"
    Option        "Monitor-DFP11" "0-DFP11"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP3" "1-DFP3"
    Option        "Monitor-DFP4" "1-DFP4"
    BusID       "PCI:6:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection[/I]

Anyone have any suggestions to send me in the right direction ?

---


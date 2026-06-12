---
title: "ATI / Intel combo (no, not a hybrid card)"
date: 2013-10-20
forum: Hardware
---

### Post by peter-katelaan on 2013-10-20
Hi there, 

I'm trying to figure out to get my three screens running again. Under Windows 7/8, I was able to use my onboard Graphics Card and my ATI graphics card in parallal- so I was able to use three screens (two attached to the ATI and one to the crappy intel one). So today I've installed 13.10 and both GPU's are recognized as follows: 

```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450]

```

And initially I had all three screens going. Well,- kind off... I had to install an other ATI Driver because I have encountered some display problems. Long story short here's the problem: When I open "Displays" only the screens attached to my AMD card are showing up. 
It's maybe worth mentioning that this only happened after I've ran the Catalyst Control Center to write the xorg.conf  (apparantly no backup configuration was saved :( ) - The third screen has power and I can see a cursor, but nothing else. 

When I use xandr I get the following output: 
```

Screen 0: minimum 320 x 200, current 3000 x 1920, maximum 3840 x 1920
DFP1 disconnected (normal left inverted right x axis y axis) <--- I guess that's my buddy screen 3 
DFP2 connected primary 1920x1080+1080+599 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       60.0  
   1152x864       60.0     75.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3     56.2  
   640x480        75.0     59.9  
CRT1 connected 1080x1920+0+0 left (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      59.9*+
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x768       59.8  
   1280x720       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  

```

I believe this happens because the xorg server doesn't know about the intel onboard card anymore. Now, how can I add the card back in? Is there any autodetect for such things (sorry if this is a noob question). 

For completeness - here my xorg.conf.
xorg.conf: 
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
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
    Identifier   "0-DFP2"
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
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3840 1920
        Depth     24
    EndSubSection
EndSection


```

Thanks in advance! 
P

---


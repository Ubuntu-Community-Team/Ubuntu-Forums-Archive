---
title: "Attempting to get dual-head working with Radeon 320M"
date: 2009-08-23
forum: Hardware
---

### Post by hellion0 on 2009-08-23
I'm having problems trying to get dual-head to work with my laptop's video card, an ATI IGP320M, also known as a Radeon Mobility U1. So far, I've managed to get a resolution of 2048x768 and a partial dual-screen effect... but with only one monitor, as the second is nowhere to be found. I'm running Xubuntu Jaunty with the "free" ATI drivers, if that helps.

My xorg.conf:
```
Section "Device"
	Identifier    "ATI 1"
        Option        "Monitor-VGA-0" "Monitor 1"
        Option        "Monitor-LVDS" "Monitor 2"
EndSection

Section "Monitor"
	Identifier	"Monitor 1"
        Option          "LeftOf" "Monitor 2"  
EndSection

Section "Monitor"
        Identifier      "Monitor 2"
EndSection

Section "Screen"
	Identifier	"Screen 1"
	Monitor		"Monitor 1"
	Device		"ATI 1"
        SubSection "Display"
          Depth           16
          # virtual screen to place
          Virtual         2048 768
        EndSubSection
EndSection
```

Output from xrandr:
```
Screen 0: minimum 320 x 200, current 2048 x 768, maximum 2048 x 1024
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+   75.0     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1024x768+1024+0 (normal left inverted right x axis y axis) 285mm x 214mm
   1024x768       60.0*+
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)
```

Only the built-in screen on the laptop (the right screen) works, even though the machine can apparently see both monitors. Please help.

---


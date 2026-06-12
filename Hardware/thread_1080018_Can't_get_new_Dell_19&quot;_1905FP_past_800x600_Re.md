---
title: "Can't get new Dell 19&quot; 1905FP past 800x600 Resolution"
date: 2009-02-25
forum: Hardware
---

### Post by Mindslant on 2009-02-25
Like the title says, I can't get new Dell 19" 1905FP past 800x600 Resolution.  Native resolution is 1280x1024.  My old CRT didn't have a problem.  Getting proprietary drivers for the nVidia card brings my resolution down to 640x600.  Any help would be greatly appreciated.  I've put below the results of lspci | grep Vga, xrandr -q and my xorg file.  I've reset the xorg file several times.

Again, thank you.

$lspci | grep VGA
$02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

$xrandr -q
$Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0


Xorg:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection

Defaultdepth 24
EndSection

---


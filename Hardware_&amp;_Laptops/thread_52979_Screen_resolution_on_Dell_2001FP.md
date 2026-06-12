---
title: "Screen resolution on Dell 2001FP"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by john deere on 2005-07-29
This is driving me nuts.

Hoary 5.04 AMD64 on a system with a GeForce 6600 GT and a 20-inch Dell 2001 FP with the native resolution of 1600x1200. I've tried to change just about anything in the xorg.conf file but I can't seem to get the res above 1024x768. Below are my current settings. Any help would be dearly appreciated.  

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync 31-80
	VertRefresh 60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by blind0wl on 2005-08-09
Maybe try changing the VertRefresh to 56-76 instead....I know the monitor runs at 1600x1200@60 only, but it might make a diference.

---


---
title: "Low hz on monitor - nvidia - new xorg configuration?"
date: 2008-07-15
forum: Hardware
---

### Post by Gentleman on 2008-07-15
Hi, I just bought a new pc and installed hardy on it... My monitor should refresh with 85hz but doesn't, after some searching I found one should disable nvidia twinview and this is a known nvidia bug. Adding that to my xorg.conf doesn't fix the problem... I can pick the correct resolution and hz in ubuntu but my monitor doesn't refresh at 85hz...

xorg.conf:

> Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"UseFBDev"	"true"
	Option		"NoLogo"	"true"
    	Option          "DynamicTwinView" "false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
EndSection

Section "Module"
	Load		"glx"
EndSection

Hardware: 

> AOC Spectrum7F (should work at 1024x768@85hz)
Geforce 7200

---


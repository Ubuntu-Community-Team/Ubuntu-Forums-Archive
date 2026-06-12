---
title: "ATI Xpress 200m Default Resolution Problem"
date: 2009-03-08
forum: Hardware
---

### Post by Nemesis02 on 2009-03-08
Hi everyone, I kinda have a small issue dealing with default resolutions with my laptop.  I have an HP Pavilion DV5000z, AMD Turion 64 ml-40 system w/ 1Gb of ram.  Now, my problem is that whenever my system loads, it loads in 2560x800 when it should be 1280x800.

I've ran into this problem at least 4 or 5 times when reinstalling Kubuntu and it all comes up after I configure the ati-settings utility for dual screen which sets it to 2560x800, however when I got single screen and disconnect the external monitor, it remains in 2560x800.

This issue is causing me to loose my desktop effects.  I cannot turn desktop effects on, or have it start when my system starts because its in 2560x800.

When the login screen appears, the xorg seems to be in 2560x800 cause i see half of the background, then the login appears on my screen just fine with the proper background fitting.  Now once I log in, the login window goes away, the background reverts to having that half background then it loads into kubuntu.

Once in kubuntu, i have the multiple desktops on, and it shows widescreen, and when i go into konsole and type xrandr, it shows 2560x800 as being the current and default resolution. When I goto system settings > display my resolution changes to 1280x800 where it should be on its own without me touching anything.  Just going to that panel changes the resolution to where it should be, and typing xrandr again tells me that the current resolution is 1280x800 and the default is 1280x800 but once I restart, I changes back to 2560x800.

Here's my xorg.conf:
```
Section "Monitor"
	Identifier	"Configured Monitor"
	ModeLine 	"1280x800_60.00" 108.88  1280 1360 1496 1712  800 801 804 836  -HSync +Vsync
	Option		"PreferredMode" "1280x800_60.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth 	24
		Modes	"2560x800" "1280x800" "1280x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection
```

Any help would be appreciated.

---


---
title: "Default Srceen Resolution (dual screen)"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by Phasmagon on 2006-12-15
Hello everyone

I have a quite trivial problem that is bothering me for days, but bare with me.

I decided to upgrade to edgy (clean install) my ASUS A7Db laptop. I managed to set up correctly the xorg.conf file for dual monitor using the radeon driver.

Here is the related portion of xorg.conf:

```
Section        "ServerLayout"
	Identifier	    "Default Layout"
	Screen		    "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		     "AIGLX" "on"
EndSection

Section "Device"
	Identifier     "ATI Radeon X700"
	Driver           "ati"
	BusID		"PCI:1:0:0"
	Option		"BIOSHotKeys" "on"
	Option		"CRT2Position" "LeftOf"
	Option		"EnablePageFlip" "on"
	Option		"MergedNonRectangular" "on"
	Option		"MergedFB" "on"
	Option		"MergedXineramaCRT2IsScreen0" "no"
	Option		"MetaModes" "1440x900-1280x1024 1024x768-1024x768 1024x768"
	Option		"MonitorLayout" "LVDS, CRT"
	Option		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon X700"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection
```

Now the problem that I am facing is that while the login screen displays at correct resolutions (1440x900-1280x1024 on dual screen and 1440x900 on single) when I login the resolution changes to 1024x768 clone mode if second screen is attached.

I have tried like a million tweaks in xorg.conf to get it to login with 1440x900-1280x1024 if dual screen or 1440x900 if single, but nothing seems to work. At the end I worked around it using an xrandr command at session manager.

The thing is I hate to work around problems, I prefer to solve them. Is there anyone who knows how?

---


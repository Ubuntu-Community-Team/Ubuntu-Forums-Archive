---
title: "915resolution with 1680x1050"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by divineleft on 2007-03-10
I recently bought a new monitor (Dell E207WFP) and i'm trying to get it to work with its optimum resolution of 1680x1050 (1280x1024 and others works). My graphics card, i865, supports all resolutions up into the 2000's so it *shouldn't* be a problem, but for some reason it is.

Every time I `startx` with everything set for 1680x1050, my monitor pops up a message reading "Cannot Open Display". Nothing shows up on the monitor, but I can tell it's working because the startup sounds of gnome work.

This is what i run for 915resolution:
> 915resolution 5a 1680 1050 16

xorg.conf:
```
Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option "ForceBIOS" "1600x1200=1680x1050"
EndSection

Section "Monitor"
	Identifier	"DELL E207WFP"
	Option		"DPMS"
	HorizSync 30-83
        VertRefresh 56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL E207WFP"
	DefaultDepth	16	
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

I just installed ubuntu today so it's a fresh install. I'd really appreciate any recommendations on what to do. Thanks.

---

### Post by divineleft on 2007-03-11
*bump* (sorry)

---


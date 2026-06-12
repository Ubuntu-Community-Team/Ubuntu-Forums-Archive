---
title: "Issue with screen panning"
date: 2009-01-09
forum: Hardware
---

### Post by Thermoman40 on 2009-01-09
I have an old AMD 2400 with a nvidia GeForce4 MX440 card. I been running ubuntu 7.04 for about a year. I was using the vesa driver for the graphics card but I wanted to run Google Earth so I installed the nvidia driver. When I restarted the screen resolution changed from 1024x768 to 800x600 and could not be changed. I tried all the usual edits to xorg.conf but nothing worked. I finally came across a posting about the monitor I have, a NFREN NF-1500MA  at [http://ubuntuforums.org/showthread.php?t=956823](http://ubuntuforums.org/showthread.php?t=956823). I tried the suggested edits to xorg.conf and the problem has been partially fixed.
The screen resolution under System > Preferences > Screen Resolution is now 1024x768 but the monitor resolution is still stuck at 800x600. As the screen resolution is too big for the monitor I have to pan around the screen to see everything. I think I'm only getting the 1024x768 resolution from adding the  "Virtual 1024 768" line to xorg.conf.
Any suggestions on how to get the screen and monitor resolutions to match at 1024x768 would be appreciated. Below is a section from my xorg.conf showing the setup.

Thanks

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "monitor-TV" "TVOutput"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
        VendorName     "Unknown"
        ModelName      "Unknown"
        HorizSync       30.0 - 110.0
        VertRefresh     50.0 - 150.0
        Option         "DPMS"
        Modeline "1024x768@60" 64.56 1024 1056 1296 1328 768 783 791 807
EndSection

Section "Monitor"
	Identifier "TVOutput"
	Option "Disable" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes "1024x768@60"
		Virtual 1024 768
	EndSubSection
EndSection

---

### Post by Blue Beard on 2009-01-09
Try "xrandr -q" to see what it thinks.  
I am not sure if this is available in 7.04.
If you have this package it will tell what the screen resolutions, virtual resolutions, device outputs and so on are.

---

### Post by Thermoman40 on 2009-01-10
> **Blue Beard said:**
> Try "xrandr -q" to see what it thinks.  
I am not sure if this is available in 7.04.
If you have this package it will tell what the screen resolutions, virtual resolutions, device outputs and so on are.
I tried "xrandr -q" and it does seem to work in 7.04. Here's what came up.

 SZ:    Pixels          Physical       Refresh
 0    800 x 600    ( 270mm x 203mm )   50  
*1   1024 x 768    ( 347mm x 260mm )  *50  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

Its not a lot of information. Does it mean anything?

---


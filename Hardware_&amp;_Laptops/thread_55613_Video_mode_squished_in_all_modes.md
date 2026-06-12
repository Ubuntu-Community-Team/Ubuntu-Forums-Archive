---
title: "Video mode squished in all modes"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by barchamb on 2005-08-09
I have a Via Epia-M motherboard with the integrated graphics.  I've tried 800x600 and 1024x768, and they are both squished on my screen.  What I mean by that is the Desktop is not taking up the whole screen.  It's almost like the Desktop thinks my monitor is a widescreen monitor or something.  800x600 fits on the screen width-wise perfect, but height-wize it is squished.  1024x768 does not fit on the screen width-wise, it hangs off the right edge, and height-wise it is also squished.

Here's what my xorg.conf file looks like:

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

1024x768, 800x600, and 640x480 are the only ones that show up in the Screen Resolution applet.

---


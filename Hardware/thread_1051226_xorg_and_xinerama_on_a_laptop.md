---
title: "xorg and xinerama on a laptop"
date: 2009-01-26
forum: Hardware
---

### Post by odinb on 2009-01-26
Hi!

Running an HP NX8440 Laptop with Intrepid, and have 2 HP LP2065 LCD monitors connected to the dockingstation. One connected to DVI, the other one to VGA, since it only has 1 DVI...

When docked I have it setup to use xinerama in 3200x1200 (resolution for each monitor is 1600x1200).

This works fairly well, except for the missing sharpness on the VGA compared to DIV, but I can live with it. Better than having limited deskspace anyway!

On the few occasions where I undock (going to a meeting etc where I need to bring the machine), I need to be able to run it on the built in LCD (resolution is 1680x1050). Doing this with my current xorg.conf, I only see the left half part of the screen.

To fix this I disable xineramam in xorg.conf and restart X.
When I get back to my dock, I then have to do the opposite, re-enable xinerama in xorg.conf. 

Is there some way I can change my xorg.conf to automatically detect this and adjust accordingly? I.e check to see if 2 monitors are present, and if so, enable xineramam, if only one monitor present, disable xineramam.

If not, any other ideas on how to fix this automatically?

This is my xorg.conf that currently works well except for not adjusting to number of screens present:

```

Section "Device"
	Identifier	"Radeon Mobility X1600-0"
	Vendorname	"ATI Technologies"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Radeon Mobility X1600-1"
	Vendorname	"ATI Technologies"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"HP LP2065-Left"
	HorizSync	75
	VertRefresh	60
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"HP LP2065-Right"
	HorizSync	75
	VertRefresh	60
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen-Left"
	Device		"Radeon Mobility X1600"
	Monitor		"HP LP2065-Left"
	DefaultDepth	24
	SubSection	"Display"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen-Right"
	Device		"Radeon Mobility X1600"
	Monitor		"HP LP2065-Right"
	DefaultDepth	24
	SubSection	"Display"
		Depth     24
	EndSubSection
EndSection

Section	"ServerLayout"
	Identifier	"Default Layout"
	Screen		"aticonfig-Screen-Left"
	Screen		"aticonfig-Screen-Right" RightOf "aticonfig-Screen-Left"
	Option		"Xinerama"	"on"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by odinb on 2009-02-06
Bump!

No one has any ideas?

---


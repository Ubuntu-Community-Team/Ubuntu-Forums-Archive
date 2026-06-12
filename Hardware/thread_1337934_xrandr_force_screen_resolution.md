---
title: "xrandr: force screen resolution"
date: 2009-11-25
forum: Hardware
---

### Post by advoss on 2009-11-25
I recently acquired a flat-panel display to replace my CRT, I have now spent all evening trying to get the new to run at a resolution higher than 800x600. I know the display supports up to 1280x1024

The best I have been able to accomplish is to have a 1280x1024 "workspace" that gets displayed 800x600 pixels at a time and will scroll when I move my mouse to the edge of the screen.

Does anyone know a way I can get all 1280x1024 pixels to display on the screen at once?

My /etc/X11/xorg.conf:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
	Option		"NoDDC" "true"
EndSection

Section "Monitor"
	Identifier	"MAG"
	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
	Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
	DisplaySize	339 271
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"MAG"
	SubSection	"Display"
		Virtual 1280 1024
		Depth	24
		Modes	"1280x1024" "1024x768"
#	EndSubSection
#	SubSection	"Display"
#		Depth	24
#		Modes	"1280x1024" "1024x768"
	EndSubSection
EndSection

```

Output from "xrandr -q":
```
Screen 0: minimum 800 x 600, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   800x600        60.0     56.0  
   1280x1024      60.0* 

```

---


---
title: "Dual Monitor setup on Intel 852GM"
date: 2008-09-07
forum: Hardware
---

### Post by Sonalchi on 2008-09-07
Greetings,

I have tried to get dual-monitors working in Ubuntu 8.04, but so far have had no such luck. I have tried the following websites for assistance, and have also checked different forums and websites but have not managed to get things working:
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

My computer is a Toshiba Tecra A1: [http://www.toshiba.ca/web/product.grp?section=1&group=223&product=1975](http://www.toshiba.ca/web/product.grp?section=1&group=223&product=1975)

Currently, my laptop is connected to a Dell 177FPb running at 1280 x 1024. Normally, the laptop display (when not connected to an external monitor) is 1024 x 768.

The output of xrandr is as follows:
```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   822x229      1319.1 +
```

My xorg.conf file looks as follows:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Is anyone able to assist me?

---


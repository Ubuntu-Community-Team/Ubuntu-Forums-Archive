---
title: "Svideo Out i810"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by brettr on 2007-01-27
Hey, I am presently trying to configure the Svideo out in my laptop, and i have tried many different configurations, but i keep getting the same error. 

No matching device section for instance (BusID PCI:0:2:1)

Here is one of the many Xorg.conf i have tried.

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"LFP"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	#Option "MonitorLayout" "TV,LFP"
	Option "XAANoOffscreenPixmaps" "true"
	#VideoRam 131072
	Screen 0
EndSection

Section "Device"
	Identifier	"intel tv"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	#VideoRam	131072
	Option	"MonitorLayout" "TV,LFP"
	Screen 1
	#Option		"TVOutFormat" "Composite"
	#Option		"TVStandard" "NTSC"
	#Option		"ConnectedMonitor" "TV"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TV"
	Option 		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"LFP"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV Screen"
	Device		"intel tv"
	Monitor		"TV"
	#DefaultDepth	24
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen  0	"Default Screen"
	Screen 1	"TV Screen" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions" 
    Option "Composite" "true"
EndSection



```

I have also tried putting in many conbinations of BusID "PCI:0:2:1" for one of the 2 Devices

Anybody help is appreciated

---


---
title: "dual montitor problem"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by gompie on 2005-04-25
sorry for posting this topic new, but all tipps from other threads did not work, or i did not see them...
i have got a hp omnibook with a ati mobility radion graphic card and i use ubuntu 5.04. now i would like to use an additional external tft monitor - and do have my problems doing so...

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)[0]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen 0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)[1]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	HorizSync	60
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor[1]"
	HorizSync	60
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
		ViewPort	0 0
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
		ViewPort	0 0
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
		ViewPort	0 0
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
		ViewPort	0 0
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
		ViewPort	0 0
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
		ViewPort	0 0
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen[1]"
	Device		"ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)[1]"
	Monitor		"Monitor[1]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen[0]"
	Screen 1	"Screen[1]" RightOf "Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```
unfortunatelly it does not work... only the external monitor shows the desktop. does anybody know where the problem is?

thanx, gompie

---

### Post by GrumpySmurf on 2005-04-26
[quote="gompie"]```
	Screen 0	"Screen[0]"
	Screen 1	"Screen[1]" RightOf "Screen[0]"
```
only the external monitor shows the desktop. does anybody know where the problem is?
[/quote]
Try,

```
Screen 0 "Screen[0]" LeftOf "Screen[1]"
Screen 1 "Screen[1]" RightOf "Screen[0]"
```

It may seem redundant, but it worked on my laptop when I was running SuSE with XFree86.  Here's the relevant parts of my XF86Config file on that system:

```
Section "Monitor"
 HorizSync    31-48
 VertRefresh  50-60
 Identifier   "LCD"
EndSection

Section "Monitor"
 HorizSync    31-121
 VertRefresh  50-160
 Identifier   "CRT"
EndSection

Section "Screen"
 Identifier "ScrLCD"
 Device "ATILCD"
 Monitor "LCD"
 DefaultDepth 24
 SubSection "Display"
   Depth      24
   Modes      "1024x768"
 EndSubSection
EndSection

Section "Screen"
 Identifier "ScrCRT"
 Device "ATICRT"
 Monitor "CRT"
 DefaultDepth 24
 SubSection "Display"
   Depth      24
   Modes      "1600x1200"
 EndSubSection
EndSection

Section "Device"
 Driver       "radeon"
 Identifier   "ATILCD"
 BusID         "PCI:01:00:0"
 Screen       1
 Option       "Rotate" "off"
EndSection

Section "Device"
 Driver       "radeon"
 Identifier   "ATICRT"
 BusID         "PCI:01:00:0"
 Screen       0
 Option       "Rotate" "off"
EndSection

Section "ServerFlags"
 Option       "Xinerama"
EndSection

Section "ServerLayout"
 Identifier   "Layout[all]"
 InputDevice  "Keyboard[0]" "CoreKeyboard"
 InputDevice  "Mouse[1]" "CorePointer"
 InputDevice  "Mouse[3]" "SendCoreEvents"
 Screen       0 "ScrLCD" RightOf "ScrCRT"
 Screen       1 "ScrCRT" LeftOf "ScrLCD"
EndSection
```

---


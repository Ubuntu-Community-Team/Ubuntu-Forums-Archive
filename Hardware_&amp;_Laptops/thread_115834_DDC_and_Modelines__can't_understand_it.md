---
title: "DDC and Modelines:  can't understand it"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by thermans on 2006-01-11
I'm running a Viewsonic G810 as the second monitor off my laptop (an Thinkpad T40 with an ATI Radeon 7500 video card).  But I can't get it to display with optimum resolution (which is 1600x1200).  It always goes to 1024x768.

There seem to be two problems:
[LIST]
[*]'ddcprobe' returns "edidfail" when I run it under Breezy, although it works under a Knoppix LiveCD.
[*]xorg seems to ignore 'HorizSync', 'VertRefresh' and 'Modeline" lines in my "xorg.conf".
[/LIST]

I can't figure out why.

Here's my 'xorg.conf' (which I tailored after reading ["Dual monitor setup on a linux laptop"]("http://ozlabs.org/~jk/docs/mergefb/"))

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Internal Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice	"Synaptics Touchpad"
EndSection
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
#	Load	"i2c"
	Load	"bitmap"
#	Load	"ddc"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Radeon Mobility 7500 (Internal)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	#Option		"DynamicClocks"	"off"
	#Option		"AGMode"	"4"
	#Option		"AGPFastWrite"	"yes"
	#Option 		"RenderAccel" "true" 
	#Option 		"AllowGLXWithComposite" "true"
	Option          "MergedFB" "true"
	Option          "MetaModes" "1024x768 1024x768-1600x1200"
	Option          "MergedDPI" "100 100"
EndSection

Section "Device"
	Identifier	"ATI Radeon Mobility 7500 (External)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	#Option		"DynamicClocks"	"off"
	#Option		"AGMode"	"4"
	#Option		"AGPFastWrite"	"yes"
	#Option 		"RenderAccel" "true" 
	#Option 		"AllowGLXWithComposite" "true"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Laptop LCD"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	HorizSync	30 - 97
	VertRefresh	50 - 180
	Modeline "640x400" 61.84 640 656 768 816 400 402 405 421  # 62 MHz, 75.8 kHz, 180.0 Hz
	Modeline "640x480" 74.17 640 656 768 816 480 482 486 505  # 74 MHz, 90.9 kHz, 180.0 Hz
	Modeline "800x600" 99.33 800 824 936 1024 600 602 607 632  # 99 MHz, 97.0 kHz, 153.5 Hz
	Modeline "1024x768" 127.26 1024 1056 1168 1312 768 770 777 808  # 127 MHz, 97.0 kHz, 120.0 Hz
	Modeline "1152x864" 142.78 1152 1192 1304 1472 864 866 874 909  # 143 MHz, 97.0 kHz, 106.7 Hz
	Modeline "1280x960" 159.08 1280 1320 1432 1640 960 962 971 1011  # 159 MHz, 97.0 kHz, 95.9 Hz
	Modeline "1280x1024" 159.08 1280 1320 1432 1640 1024 1026 1035 1078  # 159 MHz, 97.0 kHz, 90.0 Hz
	Modeline "1600x1200" 198.66 1600 1656 1768 2048 1200 1202 1213 1263  # 199 MHz, 97.0 kHz, 76.8 Hz
#	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"ATI Radeon Mobility 7500 (Internal)"
	Monitor		"Laptop LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
	Device          "ATI Radeon Mobility 7500 (External)"
	Monitor         "External Monitor"
	DefaultDepth    24
	SubSection "Display"
		Depth           24
		Modes           "1600x1200" "1024x768" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Here's the the "[Xorg.0.log]("http://www.hermans.net/Xorg.0.log")".  Note the line "(WW) RADEON(0): Failed to detect secondary monitor DDC, default HSync and VRefresh used".  See that I tried to turn "DPMS" and "DDC" off completely, but it still tries...

---


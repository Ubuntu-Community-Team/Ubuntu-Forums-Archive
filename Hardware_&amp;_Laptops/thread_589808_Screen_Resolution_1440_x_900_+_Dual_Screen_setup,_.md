---
title: "Screen Resolution 1440 x 900 + Dual Screen setup, Xorg.conf"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by stuartornum on 2007-10-24
Hi,

I have just installed LinuxMint..

Right my problem...

I came from Win XP and had a dual screen setup running off 2 video cards, however I cannot seem to get the screen to span, this has proven to be very difficult in all distro's I have used in the past.

The hardware....

1 x nVidia GeForce FX5200
1 x nVidia RIVA TNT2 Model 64
2 x Acer AL1916w (19in Widescreen TFT's, 1440x900)

Note: I can change the "ServerLayout" section to swap between using either screen 1 or screen 2, but not both at the same time.

Also I have install nvidia-glx, in xorg,conf there is the line:
```
   Load   "glx"
```

Here is my xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

############################################################################################
####### Video Cards Setup

Section "Device"
	Identifier	"NV FX5200"
	Driver		"nv"
	VendorName	"nVidia"
	BoardName	"nVidia Corporation NV34 [GeForce FX 5200]"
	BusID		"PCI:01:00:0"
	Option		"MetaModes"			"1440x900,1024x768"
EndSection

Section "Device"
	Identifier	"NV RIVA"
	Driver		"nv"
	VendorName	"nVidia"
	BoardName	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	BusID		"PCI:0:10:0"
	Option      	"MetaModes"		       "1440x900,1024x768"
EndSection


############################################################################################
####### Monitors Setup

Section "Monitor"
	Identifier	"Acer AL1916W 1"
	VendorName	"Acer"
	ModelName	"AL1916w"
  	HorizSync       30.0 - 82.0
  	VertRefresh     56.0 - 76.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Acer AL1916W 2"
	VendorName	"Acer"
	ModelName	"AL1916w"
  	HorizSync       30.0 - 82.0
  	VertRefresh     56.0 - 76.0
	Option		"DPMS"
EndSection

############################################################################################
####### Setup Video card on Monitor

Section "Screen"
	Identifier	"Screen FX5200"
	Device		"NV FX5200"
	Monitor		"Acer AL1916W 1"
	DefaultDepth	24
	SubSection "Display"
		Depth		16	
		Modes		"1440x900" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection

EndSection

Section "Screen"
	Identifier	"Screen RIVA"
	Device		"NV RIVA"
	Monitor		"Acer AL1916W 2"
	DefaultDepth	16
	SubSection "Display"
		Depth		16	
		Modes		"1440x900" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

############################################################################################
############################################################################################

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen FX5200"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Many Thanks

---


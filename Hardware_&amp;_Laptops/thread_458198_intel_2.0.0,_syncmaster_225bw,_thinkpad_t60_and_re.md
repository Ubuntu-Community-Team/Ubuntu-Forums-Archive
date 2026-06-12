---
title: "intel 2.0.0, syncmaster 225bw, thinkpad t60 and resolution"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by ningo on 2007-05-29
Hi,

Because my problem is rather complicated, I'll first explain the circumstances.

My Laptop is a Thinkpad T60, with an 'Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller' also known as intel(4) to X11.

I have a LCD on my Laptop, with a resolution of 1024x768 (the 'int. LCD') and an Syncmaster 225BW connected to my Laptop (the 'ext. LCD). EDIDs opinion about the ext. LCD:

```

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "SyncMaster"
	VendorName "SAM"
	ModelName "SyncMaster"
	# Block type: 2:0 3:fd
	HorizSync 30-81
	VertRefresh 56-75
	# Max dot clock (video bandwidth) 170 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1680x1050"	# vfreq 59.954Hz, hfreq 65.290kHz
		DotClock	146.250000
		HTimings	1680 1784 1960 2240
		VTimings	1050 1053 1059 1089
		Flags	"+HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
EndSection

```

The Goal is to use the ext. LCD only. However I tried various xorg.conf configurations. The ext. LCD is horribly blurry but is running at 1680x1050, according to xrandr. The int. LCD is always on and shows a 1024x768 fraction of the screen. So what I'm trying to do now is 1) turning the int. LCD off, and 2) removing the blurr from the ext. LCD.  I've a strong feeling that the blurr on the ext. LCD is connected to the int. LCD not shutting off.

This configuration runs fine under OpenBSD and does excactly what I want:
```

Section "ServerFlags"
#	Option		"DefaultServerLayout"	"Default Layout"
	Option		"DefaultServerLayout"	"CRT Only Layout"
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc/"
	FontPath     "/usr/X11R6/lib/X11/fonts/TTF/"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1/"
	FontPath     "/usr/X11R6/lib/X11/fonts/CID/"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi/"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi/"
	FontPath     "/usr/local/lib/X11/fonts/terminus/"
	FontPath     "/usr/local/lib/X11/fonts/proggy/"
	FontPath     "/usr/local/lib/X11/fonts/mscorefonts/"
	FontPath     "/usr/local/lib/X11/fonts/TrueType/"
	FontPath     "/usr/local/lib/X11/fonts/Type1/"
	FontPath     "/usr/local/lib/X11/fonts/misc/"
	FontPath     "/usr/local/lib/X11/fonts/texcm/"
	FontPath     "/usr/local/lib/X11/fonts/artwiz-aleczapka/"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "Extensions"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "wsmouse"
	Option	    "Device" "/dev/wsmouse"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  280   210	# mm
	Identifier   "Monitor0"
	VendorName   "LEN"
	ModelName    "4020"
	Option	    "DPMS"
EndSection

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "SyncMaster"
	VendorName "SAM"
	ModelName "SyncMaster"
	# Block type: 2:0 3:fd
	HorizSync 30-81
	VertRefresh 56-75
	# Max dot clock (video bandwidth) 170 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1680x1050"	# vfreq 59.954Hz, hfreq 65.290kHz
		DotClock	146.250000
		HTimings	1680 1784 1960 2240
		VTimings	1050 1053 1059 1089
		Flags	"+HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
EndSection

### DEFAULT ###

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	"False"
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	"True"
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
		Option      "MonitorLayout"			"CRT,LFP"
		Option      "Clone"					"true"
	Identifier  "Card0"
	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "Mobile Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Keyboard0"
	InputDevice	"Mouse0"
EndSection

### CRT ###

Section "Device"
	Identifier	"Intel 945 Graphics Controller -CRT Only"
	Driver		"i810"
	Option		"MonitorLayout"		"CRT,NONE"
EndSection

Section "Screen"
	Identifier "Default Screen -CRT Only"
	Device		"Intel 945 Graphics Controller -CRT Only"
		Monitor	"SyncMaster"
	DefaultDepth	24
	SubSection	"Display"
		Modes "1680x1050"
		Depth 24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"CRT Only Layout"
	Screen		"Default Screen -CRT Only"
	InputDevice	"Keyboard0"
	InputDevice	"Mouse0"
EndSection

```

CP'ing this file directly (and changing the mouse interface of course) tells me that some module cannot be loaded and exits. Recreating this file via X -configure and changing the interesting questions tells me "Option MonitorLayout not used"  and the situation mentioned above remains. (According to Google that's because Intel 2.0.0 doesn't use this Option anymore.) 

In summa: How can I get my ext. LCD working under Linux?

---


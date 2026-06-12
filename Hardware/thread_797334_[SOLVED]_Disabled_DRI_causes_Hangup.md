---
title: "[SOLVED] Disabled DRI causes Hangup"
date: 2008-05-17
forum: Hardware
---

### Post by knysng on 2008-05-17
I have a strange problem lately:

I'm am using a Intel Macbook Gen 1 with a Intel 945GM graphiccard. For powermanagement purposes I wanted to turn off DRI support in X. So I put this into my xorg.conf:
```
Option "DRI" "False"
```
The computer boots up fine until I reach the KDE login screen where strange graphics are being displayed followed by a crash/blackscreen. 

Can somebody explain to me what is going on. Here is my xorg.conf:

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "SendCoreEvents"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptics Touchpad" "CorePointer"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	#FontPath     "/usr/share/fonts/X11/100dpi"
	#FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "record"
	Load  "glx"
	Load  "xtrap"
	Load  "extmod"
	Load  "dri"
	Load  "dbe"
	Load  "GLcore"
	Load  "synaptics"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "SendCoreEvents"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        #Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "LeftEdge"              "10"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "10"
        Option          "BottomEdge"            "370"
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
        Option          "SingleTapTimeout"      "100"
        Option          "MaxDoubleTapTime"      "180"
        Option          "LockedDrags"           "off"
        Option          "MinSpeed"              "0.80"
        Option          "MaxSpeed"              "1.30"
        Option          "AccelFactor"           "0.05"
        Option          "TapButton1"            "0"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
        Option          "LTCornerButton"        "0"
        Option          "LBCornerButton"        "0"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "50"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
EndSection

Section "Monitor"
	#DisplaySize	  290   180	# mm
	Identifier   "LVDS"
	VendorName   "APP"
	ModelName    "9c5f"
	Option	     "DPMS"	"True"
EndSection

Section "Monitor"
	Identifier   "TMDS-1"
	Option	     "Ignore"	"False"
	Option	     "DPMS"	"True"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        Option     "DRI"                	"False"
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	# OUTH Option	    "NoDRI"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	Option	    "Monitor-LVDS"	"LVDS"
	Option	    "Monitor-TMDS-1"	"TMDS-1"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "LVDS"
	DefaultDepth	24
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
		Virtual	  1920 2000
	EndSubSection
EndSection


```

[SOLVED]

The "newer" xf86-video-intel driver force the card into AccelMethod exa which doesn't run well without 3D Dri on a 945-950GM. so:
```
Option "AccelMethod" "xaa"
```
fixed everything.
Thanks!

---


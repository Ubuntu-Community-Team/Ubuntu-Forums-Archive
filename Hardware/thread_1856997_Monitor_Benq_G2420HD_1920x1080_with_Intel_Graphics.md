---
title: "Monitor Benq G2420HD 1920x1080 with Intel Graphics Card"
date: 2011-10-09
forum: Hardware
---

### Post by titis on 2011-10-09
Hi folks
I just install in my CO Ubuntu 11.04, and works all except the VGA mode for my BenQ G2420HD Monitor, so a I did:

1. In terminal:

```
[SIZE="1"]xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00


sudo apt-get install xserver-xorg-video-displaylink
gksudo gedit /etc/X11/xorg.conf[/SIZE]
```

2. In xorg.conf add these lines:

```
[SIZE="1"]Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "BenQ"
	ModelName    "24'' widescreen"

### Start manual config 1 #################################
	HorizSync 	30-83
	VertRefresh	50-75
	Option          "DPMS"
	Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
	Modeline "1600x900_75.00"  151.25  1600 1704 1872 2144  900 903 908 942 -hsync +vsync
	Modeline "1152x864_75.00"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
### End manual config 1 ###################################

EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Core Processor Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     16
### Start manual config 2 #################################
		Modes	"1920x1080@60" "1600x900@75" "1152x864@75" "1024x768@75"
### Start manual config 2 #################################
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
### Start manual config 2 #################################
		Modes	"1920x1080@60" "1600x900@75" "1152x864@75" "1024x768@75"
### Start manual config 2 #################################
	EndSubSection
EndSection[/SIZE]
```

3. Make Default Monitor setting for highest resolution 1920x1080 (16:9)
SystemSettings/Monitor


it works for me, good luck!

---


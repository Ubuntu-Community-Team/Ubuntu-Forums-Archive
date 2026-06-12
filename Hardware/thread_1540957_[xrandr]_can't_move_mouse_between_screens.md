---
title: "[xrandr] can't move mouse between screens"
date: 2010-07-28
forum: Hardware
---

### Post by oodlesOfmoodles on 2010-07-28
I've followed the steps outlined in this HowTo: [http://ubuntuforums.org/showthread.php?t=1493143](http://ubuntuforums.org/showthread.php?t=1493143)

Right after I log in to Gnome I can move the mouse back and forth but as soon as the task bar loads, the mouse becomes jailed in the screen its in (can't move between screens).


This is my xorg.conf:

```
 Section "ServerLayout"
            Identifier     "Layout0"
            Screen      0  "DisplayLinkScreen" 0 0
            Screen  	1  "Screen0" LeftOf "DisplayLinkScreen"
            InputDevice    "Keyboard0" "CoreKeyboard"
            InputDevice    "Mouse0" "CorePointer"
            Option	    "Xinerama" "0" #Could not get this to work it has to be disable
EndSection

Section "Files"
	ModulePath   "/usr/local/lib/xorg/modules/drivers"
	ModulePath      "/usr/lib/xorg/modules/drivers"
	ModulePath      "/usr/local/lib"

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
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option      "Device" "/dev/psaux"	
	# Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
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
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Core Processor Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	Option	    "DPMS"
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

Section "Monitor"
    Identifier     "DisplayLinkMonitor"
EndSection
Section "Device"
    Identifier  "DisplayLinkDevice"
    Driver		"displaylink"
    Option  	"fbdev" "/dev/fb0"
EndSection
Section "Screen"
    Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
    Monitor         "DisplayLinkMonitor"
    SubSection "Display"
        Depth       24
        Modes       "1920x1200" "1920x1080" "1680x1050" "1600x1200" "1440x900" "1366x768" "1280x1024" "1280x960" "1280x800"  "1280x768"  "1152x864" "1024x768" "800x600" "640x480" 
    EndSubSection
EndSection

```

Any help would be appreciated. I'm so close to getting this to work!

---

### Post by lmwangi on 2010-10-25
Had the same issue. Finally got a workaround by using the python script from [here.]("http://www.ctctlabs.com/index.php/blog/detail/moving_the_mouse_between_separate_screens_in_a_single_x_session/")
Using the -n arguement switches you & your pointer out of the jailed screen. You may find it useful to bind it to a shortcut key.

---


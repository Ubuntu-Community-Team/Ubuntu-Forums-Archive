---
title: "screen/graphics configuration with xorg.conf or alternative???"
date: 2009-04-11
forum: Hardware
---

### Post by gnix on 2009-04-11
Hi,
I just installed Ubuntu and am pretty new to linux.  The installation went smoothly however I use an external monitor (Dell FPS 20 inch widescreen) and I cannot get it recognized.  Here's the strange part:  when I use the 'Screen Resolution' tool and uncheck the 'Mirror Screens' box, it correcly identifies both my laptop screen (1400x1050) and my external monitor (1680x1050).  I arrange them as I want them and then 'Apply' and it tells me to logout/in.  When I do this I get a brown screen (of death) with nothing but a mouse cursor.  (Note, I can actually log-in here, I just can't see anything).  The only way to get back to a visible environment is to drop to prompt and delete the xorg.conf file.  
I've spent the past few hours googling for help and much of what's out there tells me to edit the xorg.conf file.  My xorg.conf is basically empty (only a few lines with defaults like 'Identifier' "Default Screen" and 'Monitor' "Configured Monitor" etc).  Everything I could find on the web told me to rebuild the xorg.conf file with something like 'dpkg-reconfigure xserver-org'.  When I run this it asks me a bunch of questions about my keyboard and then quits without making any changes to xorg.conf. 

I am at the end of my rope.  I would really love to transition to Ubuntu but this has been pretty painful so-far.  Any help?

Humble thanks,

g

---

### Post by overdrank on 2009-04-12
Hi and welcome, could you give us some system specs such as graphics card and which version of ubuntu you are using?

---

### Post by gnix on 2009-04-12
Thanks for the reply,
It's the latest version of Ubuntu 8.10 (I installed from a CD I burned a few months ago, then installed all the updates).  Here's my laptop info:

PortableOne MX (ASUSTek Computer Inc)
System Model: M3Np  
Intel(R) Pentium(R) M processor 1.80GHz 
Version: x86 Family 6 Model 13 Stepping 6
American Megatrends Inc. 0204 BIOS
768 MB RAM

Intel(R) 82852/82855 GM/GME Graphics Controller, 64MB
Native laptop screen resolution: 1400x1050
Vertical refresh rate 60Hz

External monitor: Dell 20" 2005FPW at 1680x1050
Horizontal Freq: 30-83kHz
Vertical Freq 56-75Hz
Gamma 2.20

The more I think about it, I think the problem is probably that my graphics controller is not correctly specified in the xorg.conf... but I'm not sure.  I can use commands like this:

xrandr --output VGA --mode 1680x1050

which will mirror my display to the external monitor and use the correct resolution, but when I try:

xrandr --output VGA --right-of LVDS --mode 1680x1050

it gives me an error saying that that would create a screen resolution that's too large (max resolution 1680x1680).  But when I put a line into xorg.conf specifying my desired virtual resolution (3080 x 1050) and start-up, I get the brown-screen (login prompt that I can't see, as described before).

Thanks very much for your help!

g

---

### Post by gnix on 2009-04-12
FYI - when I run X -configure, it rebuilds my xorg.conf file as follows:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
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
EndSection

Section "Module"
	Load  "dri"
	Load  "xtrap"
	Load  "record"
	Load  "glx"
	Load  "dbe"
	Load  "extmod"
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
	#DisplaySize	  430   270	# mm
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL 2005FPW"
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
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
	BoardName   "82852/855GM Integrated Graphics Device"
	BusID       "PCI:0:2:0"
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
	Identifier  "Card1"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82852/855GM Integrated Graphics Device"
	BusID       "PCI:0:2:1"
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

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
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

```

which seems to be partly right.  When I boot using this as my xorg.conf it gives me a bunch of errors about video memory and BIOS and crashes so there must be some problems, but is this a good starting point?  I tried adding 'Virtual 3080 3080' to all of the Display subsections, but the aforementioned video problems won't let me boot up.

Thanks!

PS - FYI the xorg.conf file I'm currently using is basically empty:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
```

---


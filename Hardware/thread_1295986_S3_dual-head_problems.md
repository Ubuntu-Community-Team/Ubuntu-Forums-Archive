---
title: "S3 dual-head problems"
date: 2009-10-20
forum: Hardware
---

### Post by platnicat on 2009-10-20
Hello all. I have an IBM ThinkPad T23 running Linux Mint 7 Gloria with an S3 SuperSavage IX/C.

My problem is, I can't get the TV-OUT to work properly, or the dual-head support to function at all. I can use s3switch to enable CRT-OUT, but that only mirrors. I want full dual-head functionality. I absolutely hate Windoze, but I know that the card supports dual-head because it worked in XP. Also, TV-OUT doesn't scroll, and therefore only shows the top left 1/4 of the screen. I followed all the steps I could in [This Thread]("http://ubuntuforums.org/showthread.php?t=83973") but nothing works. This is my xorg.conf:  
```
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

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "IBM"
	ModelName    "IBM ThinkPad LCD"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "External"
	ModelName    "Display"
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
	Device     "Card0"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   1 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   1 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   1 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   1 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   1 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   1 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load  "dri2"
	Load  "dri"
	Load  "record"
	Load  "glx"
	Load  "extmod"
	Load  "dbe"
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

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen         "Screen0"
	Screen         "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "savage"
	VendorName  "S3 Inc."
	BoardName   "SuperSavage IX/C SDR"
	BusID       "PCI:1:0:0"
	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "NoAccel"            	# [<bool>]
	#Option     "AccelMethod"        	# <str>
	#Option     "HWCursor"           	# [<bool>]
	#Option     "SWCursor"           	# [<bool>]
	#Option     "ShadowFB"           	# [<bool>]
	#Option     "Rotate"             	# [<str>]
	#Option     "UseBIOS"            	# [<bool>]
	#Option     "LCDClock"           	# <freq>
	#Option     "ShadowStatus"       	# [<bool>]
	#Option     "CrtOnly"            	# [<bool>]
	#Option     "TvOn"               	# [<bool>]
	#Option     "PAL"                	# [<bool>]
	#Option     "ForceInit"          	# [<bool>]
	#Option     "Overlay"            	# [<str>]
	#Option     "TransparencyKey"    	# [<str>]
	#Option     "ForceInit"          	# [<bool>]
	#Option     "DisableXVMC"        	# [<bool>]
	#Option     "DisableTile"        	# [<bool>]
	#Option     "DisableCOB"         	# [<bool>]
	#Option     "BCIforXv"           	# [<bool>]
	#Option     "DVI"                	# [<bool>]
	#Option     "IgnoreEDID"         	# [<bool>]
	#Option     "BusType"            	# [<str>]
	#Option     "DmaType"            	# [<str>]
	#Option     "DmaMode"            	# [<str>]
	#Option     "AGPMode"            	# <i>
	#Option     "AGPSize"            	# <i>
	#Option     "DRI"                	# [<bool>]
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

```

Is help possible? ](*,):oops:

---

### Post by platnicat on 2009-10-22
Still no replies. And only 38 views. Hello?  :(:confused:

---

### Post by cariboo on 2009-10-23
S3 isn't supported very well, have a look [here]("http://www.s3graphics.com/en/search/search.aspx?keyWord=linux") the xinerama driver may be what you are looking for.

---

### Post by platnicat on 2009-10-23
How exactly do I use the xinerama driver? Also, I'm pretty sure something is wrong with my xorg.conf because Displays still says unknown. I also think that Gnome may not be using xorg.conf much at all. It appears to load the drivers, but won't let me do anything to my display. I can lower the resolution to 800x600, 640x480, or 320x240. My laptop panel is 1024x768, so this is perfectly reasonable. However, I'd like dual-head support because the card supports up to something like 1600x1440 on the external port, and that would really be nice. Finally, are there any better Display control panels I could use? In YDL on my old Mac with 2 video cards, x.org configuration all went through a graphical utility that was a breeze to use. I simply enabled the second card in xorg.conf and opened Displays, and there it was. There must be something like this for Ubuntu!

PS. Is there a way to get more than 4 lines of text into my signature? A Geek Code Block won't fit. :-(

---


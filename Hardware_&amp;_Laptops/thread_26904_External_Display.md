---
title: "External Display"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by henriette_holm on 2005-04-14
Hi.
I have a laptop with a ATI Radeon 9700. When I connect an external
monitor to the computer and boot it, everything works fine until Gnome
starts. Then the picture on the external monitor disappears and it
shows a "no signal" error.
Any suggestions?

-Henriette

My xorg.conf looks like this:

```

Section "Files"
       FontPath        "unix/:7100"                    # local font server
       # if the local font server has problems, we can fall back on these
       FontPath        "/usr/lib/X11/fonts/misc"
       FontPath        "/usr/lib/X11/fonts/cyrillic"
       FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
       FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
       FontPath        "/usr/lib/X11/fonts/Type1"
       FontPath        "/usr/lib/X11/fonts/CID"
       FontPath        "/usr/lib/X11/fonts/100dpi"
       FontPath        "/usr/lib/X11/fonts/75dpi"
       # paths to defoma fonts
       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
       Load    "bitmap"
       Load    "dbe"
       Load    "ddc"
       Load    "dri"
       Load    "extmod"
       Load    "freetype"
       Load    "glx"
       Load    "int10"
       Load    "record"
       Load    "type1"
       Load    "vbe"
EndSection

Section "InputDevice"
       Identifier      "Generic Keyboard"
       Driver          "keyboard"
       Option          "CoreKeyboard"
       Option          "XkbRules"      "xorg"
       Option          "XkbModel"      "pc105"
       Option          "XkbLayout"     "dk"
EndSection

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "CorePointer"
       Option          "Device"                "/dev/input/mice"
       Option          "Protocol"              "ImPS/2"
       Option          "Emulate3Buttons"       "true"
       Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "SendCoreEvents"        "true"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "auto-dev"
       Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
       Identifier      "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11
(RV350 NP)"
       Driver          "fglrx"
       BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
       Identifier      "Generic Monitor"
       Option          "DPMS"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
       Monitor         "Generic Monitor"
       DefaultDepth    24
       SubSection "Display"
               Depth           1
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           4
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           8
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           15
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           16
               Modes           "1400x1050"
       EndSubSection
       SubSection "Display"
               Depth           24
               Modes           "1400x1050"
       EndSubSection
EndSection

Section "ServerLayout"
       Identifier      "Default Layout"
       Screen          "Default Screen"
       InputDevice     "Generic Keyboard"
       InputDevice     "Configured Mouse"
       InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
       Mode    0666
EndSection

```

---

### Post by odix on 2005-04-14
Hi,
First you have to add additional modes in the config file, e.g.:
...
       SubSection "Display"
               Depth           24
               Modes           "1400x1050" "1280x1024" "1024x768" ...
       EndSubSection
...

because I think your monitor isn't able to display 1400x1050.
There is also a possibility to specify the secondary monitor specs, but I don't know how  :neutral: 

regards odiX

---

### Post by henriette_holm on 2005-04-15
Ok, now I'm almost there. I've gotten the external display to show a clone of the picture shown on the laptop display (which is what I want). Now the only problem is that the picture on the laptop doesn't fit the screen size. That results in a lot of screen movement which I find very confusing.
So how to I fit it to the screen?

New xorg.conf:

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	#FontPath	"/usr/lib/X11/fonts/Speedo"
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
	#Load	"speedo"
	Load	"type1"
	Load	"vbe"
	Load	"v4l"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"TwinView" "on"
	Option		"SecondMonitorHorizSync" "30-80"
	Option		"SecondMonitorVertRefresh" "30-80"
	Option 		"MetaModes" "1400x1050, 1280x1024"
	Option 		"TwinViewOrientation" "CRT RightOf DFP"
	Option 		"ConnectedMonitor" "DFP,CRT"

# Option "NoLogo" "true"
# Option "FlatPanelProperties" "aspect-scaled"
# Option "RenderAccel" "off"
# Option "UseEdidFreqs" "on"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth 		1
		Modes		"1600x1200" "1280x1024" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 		4
		Modes		"1600x1200" "1280x1024" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 		8
		Modes		"1600x1200" "1280x1024" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 		15
		Modes		"1600x1200" "1280x1024" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mendicant on 2005-04-15
The ATI driver is a little odd this way.  I don't think it can display different resolutions on the two monitors.  At least, this is the case when I try to display in non-clone modes.

---


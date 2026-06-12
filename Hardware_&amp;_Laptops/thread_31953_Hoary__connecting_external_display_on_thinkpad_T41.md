---
title: "Hoary:  connecting external display on thinkpad T41p - nothing seems to work"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by xanderdad on 2005-05-05
I'm having an impossible time trying to getting a proper video signal to an external display.  My system is an IBM Thinkpad T41p.  Hoary installation generated this "Device" section by default, in xorg.conf:

Section "Device"
        Identifier      "ATI Technologies, Inc. FireGL Mobility T2 (M10 NT)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

I'm trying to connect an external thinkvision L170p TFT panel on the VGA out port.  When I do this, the ext display shows a much smaller and warped version of the 1400x1050 view port that appears nicely on my laptop panel.  No good... - so I tried to tweak the display resolution to 1280x1024 on the laptop panel - the native resolution of the external TFT.  This caused the external TFT to again display an even smaller and more warped view.

I did plenty of research into how I could possibly get the Fn-F7 key to switch video output modes, but alas I discovered that this isn't supported.  The other ACPI events (suspend, hibernate) work OK, after I did some system tweaking.

Ubuntu is great, but if it can't drive an external display on my T41p, then I'll have to scrap the effort.

Can anyone help me save Ubuntu Hoary on my T41?

(BTW - I've spent some time googling and hacking xorg.conf to try and get xinerama, mergedfb, etc. working - all w/no luck.)

---

### Post by Termina on 2005-05-05
Same here, and no help on #ubuntu or these forums.

Tell me if you find a solution! For now, I'll be going back to Windows XP; you know, where it works. ;)

---

### Post by gondoi on 2005-05-13
I'm Trying to accomplish the same thing here.. I think i've gotten close.  I have it running on the external display, but not on the LCD of the laptop.  I have a desktop that appears to extend over (I can move the mouse and windows over), but it just won't display.  It's not pretty, but at least I've gotten closer.

I'll post my xorg.conf file and see if it helps, if someone else could post their xorg.conf for a similiar situation, maybe we could get this working.

The most important parts i've changed are in the Device section and the Screen section I added a Virtual.

BTW, i've only accomplished this with MergedFB, I can't get Xinerama even close to where I've gotten with this.

Thanks.

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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
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
        Identifier      "ATI Technologies, Inc. FireGL Mobility T2 (M10 NT)"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"               "4"
        Option          "AGPFastWrite"          "on"
        Option          "EnablePageFlip"        "on"
        Option          "RenderAccel"           "on"
        Option          "DynamicClocks"         "on"
        Option          "BIOSHotkeys"           "on"

        Option          "MergedFB"              "on"

        Option          "MonitorLayout"         "LVDS, CRT"
        Option          "CRT2Position"          "LeftOf"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. FireGL Mobility T2 (M10 NT)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
                Virtual         3000 1200
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
                Virtual         3000 1200
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
                Virtual         3000 1200
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
                Virtual         3000 1200
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
                Virtual         3000 1200
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
                Virtual         3000 1200
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

### Post by cyberwisdom on 2005-06-12
Same here.  Did anyone get this to work?  

I'm trying to do dual monitors on it but I don't have a good xorg.conf file to work with.

If you got it to work please post it.

Thanx!

---

### Post by venni on 2005-06-14
It's working for me. Here is a copy of my xorg.conf. With this my desktop is expanded to external LCD. 
Even though I don't have a thinkpad T41p this should work for ati cards.


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
	Option		"XkbLayout"	"is"
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
	Identifier	"Device[0]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen       	0
  	Option       	"Rotate" "off"
  	VendorName   	"ATI"
  	Option       	"MetaModes" "1600x1200, 1280x1024"
  	Option       	"MonitorLayout" "LVDS, CRT"
EndSection

Section "Device"
        Identifier      "Device[1]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Screen          1
        Option          "Rotate" "off"
        VendorName      "ATI"
        Option          "MetaModes" "1600x1200, 1280x1024"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
EndSection

Section "Monitor"
  Option       "CalcAlgorithm" "CheckDesktopGeometry"
  DisplaySize  506 379
  HorizSync    30-82
  Identifier   "Monitor[1]"
  ModelName    "Unknown"
  VendorName   "Unknown"
  VertRefresh  56-76
  UseModes     "Modes[1]"
EndSection

Section "Modes"
  Identifier   "Modes[1]"
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
	Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x1024" "1280x960" "1280x800" "1280x768" "1152x864" "1024x768" "800x600" "768x576" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      4
    Modes      "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "640x480" 
  EndSubSection
  Device       "Device[1]"
  Identifier   "Screen[1]"
  Monitor      "Monitor[1]"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen[0]"
	Screen		"Screen[1]" RightOf "Screen[0]"
	Option		"Clone" "off"
	Option		"Xinerama" "on"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---


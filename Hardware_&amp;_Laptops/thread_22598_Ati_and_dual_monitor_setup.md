---
title: "Ati and dual monitor setup?"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by Drakx on 2005-03-28
Greatings guys

any chance any one of you could help me setup my XFREE86 so that i can use both my monitors at once?


thanks

---

### Post by rsay on 2005-03-28
Here is a dual monitor config for XFree

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0 "Screen 0" 0 0
	Screen 1 "Screen 1" LeftOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptic" "AlwaysCore"
EndSection

Section "ServerFlags"
  	#Option 	"AllowMouseOpenFail" "true"
	Option 	"Xinerama" "off"
EndSection

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
  Load "GLcore"
  Load "bitmap"
  Load "dbe"
  Load "ddc"
  Load "dri"
  Load "extmod"
  Load "freetype"
  Load "glx"
  Load "int10"
  Load "record"
  Load "speedo"
  Load "type1"
  Load "vbe"
# Load "synaptics"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "keyboard"
        Option      "CoreKeyboard"
	Option	    "XkbRules" "xfree86"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "PS/2"
	Option	    "Device" "/dev/psaux"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "InputDevice"
	Identifier  "Synaptic"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "no"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Dell 1024x768 Laptop Display Panel"
	HorizSync    28-96
	VertRefresh  50-76
	Option	    "dpms"
EndSection


Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Samsung"
	ModelName    "Syncmaster"
       HorizSync    30.0 - 85.0
	VertRefresh  50.0 - 160.0
 	ModeLine "1280x1024" 135.00 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "radeon"
	VendorName  "ATI Technologies inc."
      	Option      "AGPMode"  "4"
        Option      "AGPFastWrite"  "yes"
        Option      "EnablePageFlip" "yes"
        Option      "EnableDepthMoves"  "yes"
        BoardName   "ATI Radeon Mobility 7500 M7 LW [Radeon Mobility 7500]"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "radeon"
	VendorName  "ATI Technologies inc."
	Option      "AGPMode"  "4"
        Option      "AGPFastWrite" "yes"
        Option      "EnablePageFlip" "yes"
 	Option      "EnableDepthMoves" "yes"
        Option      "DDCMode"  "yes"
	BoardName   "ATI Radeon Mobility 7500 M7 LW [Radeon Mobility 7500]"
	BusID       "PCI:1:0:0"
	Screen 1
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection


Section "Screen"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection


Section "DRI"
	Group        0
	Mode         0666
EndSection
``` 



Here is a dual monitor config for Xorg:

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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Radeon Mobility 9000 (M7 LW)"
	Driver		"ati"
	Option      	"MergedFB"  	"true"
#    	Option      	"MonitorLayout" "LVDS, CRT"
    	Option      	"CRT2Position"  "LeftOf"
    	Option      	"CRT2Hsync"     "30-85"
    	Option      	"CRT2VRefresh"  "50-160"
	Option 		"MergedXineramaCRT2IsScreen0" "false"
    	Option      	"MetaModes"     "1400x1050-1280x1024"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
EndSection



Section "Monitor"
        Identifier   	"External Monitor"
        VendorName   	"Samsung"
        ModelName    	"Syncmaster"
       	HorizSync    	30.0 - 85.0
        VertRefresh  	50.0 - 160.0
#        ModeLine 	"1280x1024" 135.00 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync        
      	Option      	"dpms"
EndSection



Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon Mobility 9000 (M7 LW)"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"External Screen"
	Device          "Radeon Mobility 9000 (M7 LW)"
        Monitor 	"External Monitor"
      	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024"
	EndSubSection
EndSection





Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Drakx on 2005-03-29
Thanks but that did not work  #-o  maybe if i give a lttile more info that might help

primary monitor

Eizo F55s can go upto 1600x1200 (not realy sure on the last part of that)

refresh rate 30-75
                    50-85

thats connected to the vga port of the X800

secondary monitor

looks like this [http://www.shoppinganimal.com/buy-unique-merchandise/6719625.html](http://www.shoppinganimal.com/buy-unique-merchandise/6719625.html)

can only do 1024x768

refresh rate 28-49
                    43-72

thats connected to the DVI port of the X800

I also have 3D support setup (ATI DRIVERS Installed)


Once again thanks

---


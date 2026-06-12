---
title: "Three screens on i810 (Toshiba Tecra Laptop)"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by andrewsawyer on 2007-06-01
Hiya,

Has anyone had any success with, or could possibly point me in the direct of information on getting two external screens working *with* the laptop screen on a laptop using an i810 chipset?

I've currently got the laptop screen and one other working fine (no compiz), however I'd like to see if I can get another running too.  The laptop has a docking station with the monitor running off the VGA out on the dock.  It also then has a DVI out and there is the VGA on the laptop itself.

I'm not even sure if this is possible, but I'm keen to give it a go.  Any info would be much appreciate.  My xorg.conf is as follows:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier "LCDMonitor"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LaptopScreen"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCDMonitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"LaptopScreen"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"LCDMonitor"
	Device		"LCDMonitor"
	Monitor		"LCDMonitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024" "1024x768" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LaptopScreen"
	Device		"LaptopScreen"
	Monitor		"LaptopScreen"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1280x1024" "1024x768" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDMonitorandLaptopScreen"
	Screen		0 "LaptopScreen"
	Screen		1 "LCDMonitor" RightOf "LaptopScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDMonitorandLaptopScreen"
EndSection
```

---

### Post by andrewsawyer on 2007-06-01
As a quick update, I've got three screens working, but it is on 2 devices (if that makes sense).

Below is my xorg:

```
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dbe"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"  
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"         
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"  
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"  
EndSection

Section "Device"
	Identifier "LCDMonitor"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LaptopScreen"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP,CRT"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCDMonitor2"
	Driver "i810"
	Option "MonitorLayout"	"LFP,CRT"
	Option "DDCMode" "True"
	Screen 2
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCDMonitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"LaptopScreen"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"LCDMonitor2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"LCDMonitor"
	Device		"LCDMonitor"
	Monitor		"LCDMonitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024" "1024x768" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LaptopScreen"
	Device		"LaptopScreen"
	Monitor		"LaptopScreen"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1280x1024" "1024x768" 
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LCDMonitor2"
	Device		"LCDMonitor2"
	Monitor		"LCDMonitor2"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024" "1024x768" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDMonitorandLaptopScreenandLCDMonitor"
	Screen		0 "LCDMonitor"
	Screen		1 "LaptopScreen" RightOf "LCDMonitor"
	Screen		2 "LCDMonitor2" RightOf "LaptopScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDMonitorandLaptopScreenandLCDMonitor"
EndSection
```

The left screen appears on the monitor to the left of my laptop like it should.  The middle screen appear on my laptop display like it should.  The right screen also appears on my laptop screen.  The screen isn't squashed or anything.  The mouse just scrolls off the right side of the laptop monitor and reappears on the left side.  So all I have to do it get the far right to appear on a new device.  Any suggestions?

---

### Post by andrewsawyer on 2008-01-15
Bump

---


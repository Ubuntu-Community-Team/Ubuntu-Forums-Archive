---
title: "serial stylus help in HH"
date: 2008-06-11
forum: Hardware
---

### Post by Revfisk on 2008-06-11
Following this thread: [http://ubuntuforums.org/showthread.php?t=590747](http://ubuntuforums.org/showthread.php?t=590747)

I've tried setting up my x41 tablet.  The tutorial worked for me in Gutsy, but not now in HH.  When I type xidump stylus is reports that it cannot find the stylus.

gedit x11/xorg.conf looks like this right now:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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



Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "stylus"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "eraser"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "cursor"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"

EndSection

****
Any thoughts as why my stylus is not recognized?  Help???:confused:

---

### Post by Revfisk on 2008-06-11
Anyone?

---


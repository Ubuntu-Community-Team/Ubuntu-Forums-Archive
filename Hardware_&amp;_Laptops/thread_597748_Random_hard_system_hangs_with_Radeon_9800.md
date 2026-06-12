---
title: "Random hard system hangs with Radeon 9800"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by joelholdsworth on 2007-10-30
Hi There,

I'm having a problem right now where my system seems to hang totally at random. I'm running dual screen with randr in Gutsy Gibbon on my Radeon 9800 Pro, with compiz enabled, and I'm using the open source "radeon" driver. I strongly get the impression that this is a video driver issue - it didn't seem to be a problem before I enabled dual screen.

Sometimes the system hangs after 2 minutes - sometimes after 40. There doesn't seem to be any trigger that I can reproduce, and the system seems to hang hard so that Ctrl+Esc, Ctrl+F# and Ctrl+Alt+Del are all unresponsive.

Does anyone know what might cause this?

Thanks
Joel


----------
Here's my xorg.conf:

> Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option          "monitor-VGA-0"   "VGA"
	Option		"monitor-DVI-0"   "DVI"
EndSection

Section "Monitor"
	Identifier	"VGA"
	Option		"DPMS"
	Option		"Gamma" "0.65"
EndSection

Section "Monitor"
	Identifier	"DVI"
	Option		"DPMS"
	Option		"Gamma" "0.65"
	Option		"Below"  "VGA"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"VGA"
	DefaultDepth	24
        SubSection "Display"
           Depth		24
           Virtual              2048 2048 
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by TrueLens on 2007-10-30
I don't have a solution to your problem but would just like to say I'm seeing the exact same thing with the hard system hangs.  I'm using the new ATI 8.42.3 driver with a Radeon 9800.  Different driver with the same symptoms.  I wonder if it is not the video driver but perhaps something else.

---


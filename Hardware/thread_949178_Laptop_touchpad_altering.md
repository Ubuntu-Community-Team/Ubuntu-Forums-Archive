---
title: "Laptop touchpad altering"
date: 2008-10-15
forum: Hardware
---

### Post by NFITC1 on 2008-10-15
I've got a touchpad on my laptop running 8.04 and it won't let me configure it in such a way that it won't left-click if I tap the pad. I've been looking for other topics, but none have this specific issue. I think I need to change my xorg.conf to allow a touchpad, but that's not currently there. Here's my input devices in my xorg.conf:

```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

	# /dev/input/event
	# for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

	# /dev/input/event
	# for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

	# /dev/input/event
	# for USB
	Identifier  "cursor	"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

```

lshw says nothing about it. Any suggestions?

---

### Post by Amorget on 2008-10-15
I don't know what type of touchpad you have, if it's a Synaptic here is the code from my Xorg.conf  I replaced the "Mouse" device section with this, and I made sure to change in the "Server Layout" section the "Configured Mouse" to "Synaptics Touchpad"

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

---


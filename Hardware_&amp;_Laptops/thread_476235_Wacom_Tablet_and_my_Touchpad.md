---
title: "Wacom Tablet and my Touchpad"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by Anaea on 2007-06-17
This isn't a very serious problem but it is a bit annoying.  I just got a Wacom Grapphire4 tablet, got it configured so that it's working in GIMP, but it's messing up my touchpad.  Normally I can click and drag with my touchpad by tapping, and scroll with the far right side of my touchpad.  If my tablet is plugged in (USB) while X starts then I lose those functions on my touchpad.  If I plug in the tablet after X starts it works like a mouse and I don't lose any touchpad functionality, but my tablet isn't very functional.  I'm guessing that X is recognizing either a touchpad or a tablet but not both at once and I'm stuck with whichever it detects as it starts.  Is there a way to have it recognize both at once?  

I have the latest wacom-tools from the repos installed, and the relevant parts of my xorg.conf are:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

---

### Post by Anaea on 2007-06-17
Never mind.  Two reboots later it all works the way it ought to.

---


---
title: "Black video on external display?"
date: 2008-05-04
forum: Hardware
---

### Post by jobsonandrew on 2008-05-04
Hi all,
I just connected my laptop to a TV, and after changing the resolution and restarting X (log out and back in) all worked well..

That is, until I play a video in totem.. the video appears on the laptop display but not the TV?? im pretty sure this is something to do with overlays.. but i dont know how to set up xorg.conf properly.. here is what i have:
```

#a few comments
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

I noticed that if i remove the lines:
```
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
```
from the 'device' section, then the video appears on both screens at the same time, but the video is very blocky (i put those lines in to combat the blockiness problem)..

Anyone know how to configure the xorg.conf for this type of problem, or does anyone know of a good site that REALLY explains what the options for xorg.conf are and what they do?

Thanks

---


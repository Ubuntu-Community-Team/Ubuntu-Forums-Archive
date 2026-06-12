---
title: "Touchpad not working"
date: 2008-09-13
forum: Hardware
---

### Post by andre.kappes on 2008-09-13
Hello,

I have some troubles with my touchpad on my Acer Aspire 5520G Notebook. Recently I reconfigured my xserver (using dpkg-reconfigure xserver-xorg). Now, my touchpad is not working any longer, though it should be configured correctly in xorg.conf

Maybe someone can help me with this? I would be grateful for a useful hint!

Thanks,

André

P.S.: Here is a listing of my xorg.conf...
----
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Option          "SHMConfig"             "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
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

---

### Post by Infinite Indefinite on 2008-09-13
I'm using an Acer Aspire 3104NWLMi, and my xorg.conf, has the following:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"	"on"
	Option		"TappingOff"	"1"
	Option		"MaxTapTime"	"0"
EndSection

I noticed that your xorg.conf states "HorizEdgeScroll" rather than "HorizScrollDelta" - could that be the problem?

---


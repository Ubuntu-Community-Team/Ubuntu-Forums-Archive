---
title: "Synaptics doesn't work until x is restarted"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by Xenogis on 2007-03-19
In ubuntu the normal mouse drivers get control of my mouse until I restart X, then synaptics works fine. This doesn't happen in Slackware or Gentoo. The mouse also works fine on the live cd which is really weird. Here is my xorg.conf (the relevant parts anyways)

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"dbe"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
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
	Option		"HorizScrollDelta"	"1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad" "SendCoreEvents"
	Option		"AIGLX" "true"
EndSection

```

---

### Post by apjone on 2007-03-19
Boot the live cd and compare the xorg.conf. That may shed some light. That's all i can suggest as i have not experienced this problem

---


---
title: "Dell Studio1535 refuses to use 1280x800 res"
date: 2008-10-13
forum: Hardware
---

### Post by strm on 2008-10-13
Hi,
After several days of fighting with drivers and resolutions on this laptop (gfx: 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series [1002:95c4]) I've decided to come here. First I'll mention that for some reason, under System > Administration > Hardware Drivers, ATI accelerated graphics driver is not enabled, but is in use (strange). Now, here are the contents of my xorg.conf file (unfortunately only 1024 and 800 modes are available at the moment). Some help would be appreciated. Thanks.
```

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
	DefaultDepth	24
	Subsection "Display"
		Viewport   0 0
		Modes "1280x800" "1024x768" "800x600"
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---


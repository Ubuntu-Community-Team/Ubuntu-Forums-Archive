---
title: "No graphic acceleration with a big desktop (Dual screen)"
date: 2008-08-12
forum: General Help
---

### Post by Oweran on 2008-08-12
Hello,

First of all, I'm not fluent in english so I appologize in advance if my english is not perfect.
I've got an issue that really bother me. I have two screens and I'm able to have a "big desktop". With xinerama.

Here's my xorg.conf :


```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
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
	Option "MetaModes" "1280x1024-1280x800 720x400-640x480"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
Subsection "Display"
		Virtual 2560 1824
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
		Option "Composite" "Enable"
	EndSection
```

The chipset I use is : ```
lspci | grep "VGA"
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```

But when I use xinerama, I don't have direct rendering (direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
When I remove the lines about the big desktop in xinerama, I have the direct rendering, and about 900 FPS with "glxgears".

I read some post who said that Xinerama doesn't works with Graphic Acceleration, but that was in 2005... No changes ?

Thanks in advance for the answers,

A new member of the Ubuntu community. ;)

P.S : Hoping I'm in the right section.

---

### Post by Oweran on 2008-08-12
Sorry, it's Xrandr, not Xinerama.
I heard that Xinerama doesn't work with acceleration but Xrandr does. Or it should. Yeah... should...

---

### Post by Oweran on 2008-08-13
No ideas ? ...

---


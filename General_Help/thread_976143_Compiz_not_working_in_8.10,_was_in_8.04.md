---
title: "Compiz not working in 8.10, was in 8.04"
date: 2008-11-09
forum: General Help
---

### Post by danradigan on 2008-11-09
Compiz with 8.10 is not working on my XPS M1330.   Things seemed to work just fine under 8.04.  When I start it in 8.10 from the command line I get this:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

xorg.conf is as follows:

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
#	InputDevice	"Synaptics Touchpad"



Dan

---

### Post by ieBrazil on 2008-11-09
sorry, that's Greek for me! Lay person sucks.

good luck!

I will stay on using my Hardy Heron...

---

### Post by eternalnewbee on 2008-11-09
> Compiz with 8.10 is not working on my XPS M1330. Things seemed to work just fine under 8.04
Have you enabled your Hardware Driver?
To check, go to: **Main Menu > System > Administration > Hardware Drivers**

---

### Post by Peter09 on 2008-11-09
If you cannot see any hardware drivers to enable boot into recovery mode and try the xfix option. The look again for drivers to enable. If no luck then post the output of

```
lshw -C display
```

---


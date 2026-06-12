---
title: "Intel X3100, Dual monitors, cloned"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by picopir8 on 2007-08-17
I have a laptop with the X3100 chipset.  I am running Feisty but downloaded the Gutsy drivers.   All is working fine except I am unable to get both the laptop display working simultaneously with an external monitor (I dont want to span desktops, I just want to clone the display so I can hook up the laptop to a projector and see the same thing on both the projector and the laptop display).

The following code for xorg.conf gets me most of the way there.  It clones the display for the login screen but as soon as I login, it goes to the external display only.  fn-F4 does not appear to do anything having BIOSHotkeys enabled.

Does anyone know what I need to do to get both displays working once I log in?  I know that I only have one video card section and one screen section,  but this "mostly" works as I do get two video feeds at the login screen so I dont really think multiple entries are required.  Also, if I can get fn-F4 working, that would be great, but I would be happy with both displays being active simultaneously.

> Section "Device"
	Identifier	"Generic Video"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option "monitor-VGA" "VGAOutput"
	Option		"BIOSHotkeys"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"VGAOutput"
#	Option "RightOf" "LVDS"
#        Option "Disable" "true" # uncomment for laptop display, comment out for external display
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Generic Screen"
	Device		"Generic Video"
        Monitor         "Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24			
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Generic Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by bstilgerindustries on 2007-12-07
try hooking up the monitor / projector, then restart the x server with ctrl + alt + backspace.  works on my toshiba with X3100.

---

### Post by victorgreen on 2007-12-07
WIth gutsy on x3100 in an X61, I have to plug in the monitor or projector and then restart, restarting x didnt cut it.

---

### Post by cprophecy on 2008-02-04
might be kind of an old post, but.. i have an x61 thinkpad with the same video card. running into the same issue. of course you can restart X, but shouldnt it be easier than this to change to an external monitor and back? ie. be able to press the Fn-F7 button, or run the xrandr command?

---


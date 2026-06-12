---
title: "getting double-clicks for single taps with alps trackpoint and generic mouse driver"
date: 2008-08-30
forum: Hardware
---

### Post by ireneshusband on 2008-08-30
I am trying to use the x.org generic mouse driver ("mouse") with the ALPS trackpoint on my Thinkpad R61i. The reason for this is because the Synaptics driver doesn't support middle-button scrolling, and in any case, I have had to disable the touchpad in bios in order to get access to the trackpoint features.

The problem I am having is with left-click, meaning both a click on the left trackpoint button or a press on the trackpoint itself (because I have the press-to-select feature enabled). With the xorg.conf created by the Ubuntu installer, which used the synaptics driver, this worked fine. However with the generic mouse driver each such click is doubled. This means, for instance, that every time I click on a word in firefox or thunderbird, it gets highlighted.

Here are the two sections of xorg.conf in question:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "InputDevice"
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Emulate3Buttons"	"true"
	Option		"EmulateWheel"		"on"
	Option		"EmulateWheelButton"	"2"
EndSection


And here is the server layout as it stands now:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
#	InputDevice	"Synaptics Touchpad"
	InputDevice	"Generic Mouse"
EndSection


So in short, does anybody know how to get the ALPS trackpoint working properly with all its features enabled, either with the generic mouse driver or with something else? I'm not bothered about getting the touchpad working at the same time because I'm finding life a lot easier without it.

---

### Post by ireneshusband on 2008-08-30
I have confirmed that xev picks up double press and release events:

ButtonPress event, serial 31, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 24288257, (92,103), root:(909,152),
    state 0x10, button 1, same_screen YES

ButtonPress event, serial 31, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 24288257, (92,103), root:(909,152),
    state 0x110, button 1, same_screen YES

ConfigureNotify event, serial 31, synthetic YES, window 0x4400001,
    event 0x4400001, window 0x4400001, (815,47), width 178, height 178,
    border_width 2, above 0x1200318, override NO

ButtonRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 24288446, (92,103), root:(909,152),
    state 0x110, button 1, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 24288446, (92,103), root:(909,152),
    state 0x10, button 1, same_screen YES



I can also confirm that I do not have two mouse sections in my xorg.conf sharing the same name, which has often been a cause of such problems for other people.

---

### Post by ireneshusband on 2008-08-30
The problem stems from the fact that xorg.conf nowadays behaves very differently from how xorg.conf and its predecessor XF86Config behaved in the path. Nowadays the server configuration is determined largely by hardware detection when X starts up. This means that what you specify in the server layout section of xorg.conf may not be what you get.

With regard to the specific problem at hand, inserting the following in the relevant inputdevice section prevented an automatically generated mouse device from being layered on top of the one I configured:

Option "CorePointer" "true"

---


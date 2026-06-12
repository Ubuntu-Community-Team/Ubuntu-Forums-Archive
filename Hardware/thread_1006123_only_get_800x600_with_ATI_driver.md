---
title: "only get 800x600 with ATI driver"
date: 2008-12-09
forum: Hardware
---

### Post by cjh19460 on 2008-12-09
I am new to this so I find lots of it mystifying -

I have an HP laptop, HPPavillion DV8000 with an ATI Radeon Xpress 200M video chipset.  It has a wide screen with a native resolution of 1440x900.  I was using the flgrx drivers but had problems - I could not enter consoles with ctrl-alt-F1, etc, and also rendering in Google Earth didn't work very well.  I decided to try open source, so I followed the directions in this:

[URL="https://help.ubuntu.com/community/RadeonDriver"]
https://help.ubuntu.com/community/RadeonDriver[/URL]

I can get the consoles now, but even with the xorg.conf edits, restarts, etc I cannot get any resolution except 800x600. On System/Prefrences/MonitorResolution, the resolution dropdown only offers 800x600.

Can anyone tell me why?

thanks - Carl

xorg.conf is as follows:


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
	Identifier	"Radeon Xpress 200M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon Xpress 200M"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection	"Display"
		Depth		24
		Modes		"1440x900" "1024x768"
	EndSubSection

EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section	"DRI"
	Mode 0666
EndSection

Section	"Extensions"
	Option	"Composite" "Enable"
EndSection

---

### Post by phidia on 2008-12-09
I'm not an expert on ATI cards-they have more recently been providing drivers for linux. You might have the best luck with installing envyng and using that to install the driver for your card.

Before doing that though have you tried opening System > Administration > Hardware Drivers and seeing if you have the option there of enabling the ATI driver?

---


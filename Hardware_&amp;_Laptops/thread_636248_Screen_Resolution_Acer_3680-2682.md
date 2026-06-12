---
title: "Screen Resolution Acer 3680-2682"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by robskicks on 2007-12-09
I'm a newbie to Ubuntu, so you're going to have to walk me through this...

I have Acer Aspire 3680-2682... I changed the OS to Ubuntu after vista crapped out... My biggest concern is my screen resolution just does not look right. It is supposed to be 1200x800 but it seems the biggest option I have is 1024x768. This pulls my screen so that all pictures are kinda wide, etc. 

How can I get my screen to look right?

I tried searching the forums but I don't know much about changing the code, so I'll need step by step instructions on how to do this. Any help I get is greatly appreciated.

---

### Post by instance on 2007-12-10
Good luck :( I'm still looking for reliable "mostly know what I'm doing" instructions for the same issue on an Acer TravelMate 6592.

So far the closest I've found is [https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/57525](https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/57525) which includes this comment:
> Cool, okay thanks. Since we've got one bug canceling out the other, I'm putting this at low priority. We probably needn't worry about fixing it since we intend to chuck xreprobe in Hardy anyway, but lets leave this bug open anyway for the record. When we drop xresprobe we'll probably go through and WONTFIX this and any other remaining bugs.

I will find a way to fix this one way or another. Will update this thread if I can.

---

### Post by VVebbie on 2007-12-10
Speaking as a moderately incompetent linux user, probably the most useful thing you can do if you are looking for help with this is to post the contents of your /etc/X11/xorg.conf file.

---

### Post by instance on 2007-12-11
Okay, I have a TravelMate 6592-6034. The install xorg.conf looks like this:

> Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


sudo get-edid | parse-edid reports
> 
	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	Identifier "AUO:7420"
	VendorName "AUO"
	ModelName "AUO:7420"
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1280x800"	# vfreq 60.002Hz, hfreq 49.382kHz
		DotClock	71.110000
		HTimings	1280 1328 1360 1440
		VTimings	800 803 809 823
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
EndSection


xresprobe vesa reports:
> id: 
res: 
freq: 
disptype: lcd/lvds


Pasting the edid output into the monitro section of xorg.conf results in a blank screen.

---

### Post by AJB2K3 on 2007-12-11
have you try the 915 resolution patch?

---

### Post by instance on 2007-12-11
AFIK That patch applies to Intel cards, this is an ATI, so no.

---

### Post by shadows123 on 2007-12-31
Same prob here..
I have 1680x1050..
Doesn't look good like this..
My bro had done it via nvidia thing but he always has to do a restart xserver  command when starting ubuntu..

---


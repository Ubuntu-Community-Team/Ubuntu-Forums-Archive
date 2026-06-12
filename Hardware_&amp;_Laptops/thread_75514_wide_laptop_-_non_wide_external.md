---
title: "wide laptop - non wide external???"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by pepster on 2005-10-13
Hi,

I have a widescreen laptop (HP nx8220). I have not found a way to get the external non wide monitor working - when I change the resoultion down it still shows only part of the screen on the external monitor.

Perhaps someone can suggest what magic I need in my Xorg config file.
Below is my current setup.

Thanks, Joseph


Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Driver		"ati"
	BusID		"PCI:1:0:0"   # vendor=1002, device=3150
EndSection 

Section "Monitor"

    Identifier    "WXGA"
    Option         "DPMS"
    HorizSync      31.5 - 50.0
    VertRefresh    40-90
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Monitor		"WXGA"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by pepster on 2005-10-13
I am sad to report  that windows XP handles the external monitor without a problem, either as a mirror or extension.


-JOseph

---


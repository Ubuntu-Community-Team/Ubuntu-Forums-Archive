---
title: "Mouse Config"
date: 2005-02-26
forum: Hardware &amp; Laptops
---

### Post by trivialpackets on 2005-02-26
Here's my issue, I've been working on this for a bit now.  I think I've got my mouse configuration in xorg set up, but I'm still not able to use the mouse.  I'll post below for input.  My most recent discovery is that when the system boots up, the logitec wireless adapter has power.  When you press the reset button, a little light on it starts flashing, but then stops.  Now, when ubuntu loads up, the reset button no longer does anything and it seems as though there is a loss of power somehow within my configuration?  Any ideas?


Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
	Option 		"CorePointer"
	Option 		"Device" 		"/dev/input/mice"
	Option 		"Protocol" 		"ImPS/2"
	Option 		"Emulate3Buttons" 	"true"
	Option 		"ZAxisMapping" 		"4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 440 Mac/GeForce 440 Go 64M]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"	
	Identifier		"Default Layout"	
	Screen			"Default Screen"	
	InputDevice		"Generic Keyboard"     		"CoreKeyboard"	
	InputDevice		"Configured Mouse"       	"CorePointer"	
	InputDevice		"Synaptics Touchpad"    	"AlwaysCore"
EndSection


Section "DRI"
	Mode	0666
EndSection

---


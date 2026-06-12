---
title: "Screen resolution on Acer 1524"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by xristos on 2005-06-02
I own an Acer 1524 that has a 15,4 Wide XGA TFT Monitor . In Windows it works at 1280x800@60Hz . 
In Ubuntu screen resolution says that it works at 1280x768@60Hz .
How can I make that 768 to 800 ???

Here is my xorg.conf file : 

Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX Go 5700]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
	#DisplaySize     338 203 # 1280x800 96dpi
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36 [GeForce FX Go 5700]"
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
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---


---
title: "Do I need ATI drivers? which ones?"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by byen on 2005-07-18
Hey guys,
Ok.. I have a ATI radeon U1 Mobility graphics card using the radeon 7500 series graphic card. How do I know if I need to install drivers for my graphic card or not? Have no major issues with the way things are going on but do not really know if the card is being used or not. Can someone guide me though this:My Xorg says:
> Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

[COLOR=Blue]Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection[/COLOR]

[COLOR=Sienna]Section "Monitor"    (_have an LCD laptop monitor...can i do something here)_
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection[/COLOR]

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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

Thank you for your help and support.

---

### Post by mad_scientist03 on 2005-07-18
You can try the command "glxgears" to give you a benchmark of your OpenGL capabilities. You can try to search the web to see what other people are achieving (the program gives you an output in frames per second). According to your xorg.conf file, you are using the ati driver, which seems to be correct given your hardware. You can always check ATI's website out for newer releases of their driver than the one Ubuntu is providing. Other than that, if it ain't broke, don't fix it.

---

### Post by byen on 2005-07-18
[QUOTE=mad_scientist03]You can try the command "glxgears" to give you a benchmark of your OpenGL capabilities. You can try to search the web to see what other people are achieving (the program gives you an output in frames per second). According to your xorg.conf file, you are using the ati driver, which seems to be correct given your hardware. You can always check ATI's website out for newer releases of their driver than the one Ubuntu is providing. Other than that, if it ain't broke, don't fix it.[/QUOTE]
 yeah..its working ok so I guess i better leave it alone. thanks.

---


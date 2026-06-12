---
title: "I need help to get my TV work"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by goood on 2008-02-10
I got a HDTV-Ready TV (LG LS19D4) for christmas.
And I have a DELL Inspiron 6400 (with an ati X1400).

My laptop has a maximum resolution of 1280x800 and the TV 1440x900.
Now I want my "Desktop" on the TV with a resolution of 1440x900 if I plug in the cable and I want to have my "Desktop" on my Laptop if I detach the cable. Currently I'm only able to use a cloned "Desktop" on my TV and I can't see the whole "Desktop" on my TV (i'm sure that it's not an extension of the desktop).

Currently I'm using: 
Kubuntu 7.10
KDE 3.5.8
Xorg 1.3
$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

I hope someone can help me.
Thanks

Here's my xorg.conf

> 
Section "Files"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"nodeadkeys"
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

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option  	"EnablePageFlip"	"true"
	Option		"DynamicClocks"		"true"	
	Option		"UseInternalAGPGART"	"no"
	Option		"NoTV"			"no"
	Option		"TVStandard"		"PAL-D"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	Modeline	"1440x900@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
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

### Post by oldsoundguy on 2008-02-10
first question that has to be answered.  Do you have a DVI-D output on the laptop?

---

### Post by goood on 2008-02-10
I only have a VGA output.

---

### Post by oldsoundguy on 2008-02-10
that could be the problem .. along with the set up of the second screen in your driver utilities.  VGA is not television. S-Video and DVI are television .. and S-Video sometimes has issues with wide screen. (mine does)

---

### Post by goood on 2008-02-11
Does that mean that I don't have a chance to get the TV work with 1440 x 900 if I have a VGA and a S-Video output?

---

### Post by oldsoundguy on 2008-02-11
good chance you are stuck with it as is unless you get an nVidia Quadro card.  They have dual DVI outputs. (what I did). (card was originally targeted for CAD users)  Regular cards with the svideo and vga as the outputs are just fine for standard aspect ratio sets.  I used same for years when I was running ATI cards on WinDOZE.  
Now, mind you, the Quadro is not a super whizz bang GAMING card (good, but not great for uber gaming).  It is a DISPLAY card

If you upgrade technology on one section of your system, you have to think about the extra costs to implement that upgrade with added hardware.

Since it IS an added screen and your current monitor system for your computer is working as it should, it is one of those things you can WAIT to complete if needed.

---

### Post by goood on 2008-02-14
Than I'll stick to my laptop  ;-)

Thx guys

---


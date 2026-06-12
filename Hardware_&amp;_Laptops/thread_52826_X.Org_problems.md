---
title: "X.Org problems"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by zacman on 2005-07-29
I have an hp dv1000 laptop with hoary.  Pretty much everything was auto configured and worked except for X.  No working video at all after the install.  X is only working with the "vesa" driver.  It has an "Intel Graphics Media Accelerator 900".  I've read numerous reports of people using the i810 driver, and that is, in fact, what ubuntu configures it with durring installation, but all I get is a black screen.  Any help much appreciated.

Relevent lines from lspci:

0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)


Current Xorg.conf file:

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

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
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

### Post by baza41 on 2005-07-29
Welcome to the wonderful world of Xorg on Hoary. My Dell laptop, Inspiron 2200, configures for the i810, but still blank screens unless I switch to the VESA driver. From the outset of the switch to xorg from xfree86 Ubuntu has had big problems with configuring X11. 

I really hope that this will get fixed in Breezy, but on a test install last night... blank screen... again. 

I'm not knocking Ubuntu here, but this intel chip problem will put a lot of people off from using it if it does not get sorted; not everyone likes to hack around with config files, your normal joe-blow wants it all to work, 'out of the box'. 


B

---

### Post by supanova on 2005-08-01
Hi

I bet if you install Fedora Core 4 you'll have the same problems. I know that I did

I have an integrated 865GV chipset.... It's more related to Xorg and the i810 driver. One must remember that underlying each distro is still an amalgamation of a number of opensource projects.

Ubuntu is a great distro... give it a chance

Ciao

---

### Post by zacman on 2005-08-05
If anyone has an HP DV1000 and is having Xorg problems look [here](http://www.ubuntuforums.org/showthread.php?t=54544)

---


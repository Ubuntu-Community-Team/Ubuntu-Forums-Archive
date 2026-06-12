---
title: "DVI display problem"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by falcone on 2005-09-23
Hi everyone, i think the regulars would be sick of this question already but i still cannot figure it out. I'm using a Philips 105E CRT connected via RGB and a (really old)Gateway FPD1500 connected via DVI with a DFP convertor, and am trying to do a dual display setup, though i would be happy just to have my LCD display something at least right now :x

here is my xorg.conf :

################################################
#                      X Configuration File                      #
#         Created by YanC42 0.0.9 (23-09-2005 17:00:00)          #
#               (c) 2002-2005 by Sebastian J. Wolf               #
#        Licensed under GNU General Public License (GPL)         #
#     [http://yanc.ygriega.de/](http://yanc.ygriega.de/) - [http://yanc.sourceforge.net/](http://yanc.sourceforge.net/)     #
################################################

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


Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
Option "NvAGP" "1"
Option "NoLogo" "1"
Option "TwinView" "1"
Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480"
Option "TwinViewOrientation" "LeftOf"
Option "SecondMonitorHorizSync" ""
Option "SecondMonitorVertRefresh" ""
Option "ConnectedMonitor" "DFP,CRT"
Option "TVStandard" "NTSC-M"
Option "TVOutFormat" "COMPOSITE"
EndSection


Section "Monitor"
	Identifier	"105E"
	Option		"DPMS"
HorizSync 30 - 61
VertRefresh 56 - 75
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"105E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


Section "DRI"
	Mode	0666
EndSection




the configuration was done using YanC and I'm not sure if it is doing it right. And the scanning frequency is pretty much some guess work..

another thing i'm not sure if its related is that my LCD display wouldn't display the BIOS POST, only my CRT. my LCD only starts once on the windows desktop. so stuff like the grub loader etc is only viewable on my CRT.

any one got any ideas?

thanks in advance! :D

---


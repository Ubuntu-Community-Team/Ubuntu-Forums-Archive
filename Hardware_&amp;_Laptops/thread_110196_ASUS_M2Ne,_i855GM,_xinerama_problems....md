---
title: "ASUS M2Ne, i855GM, xinerama problems..."
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by piopawlu on 2005-12-30
Hello,

I've been trying to run xinerama for three nights already, and still no success getting 'wide-desktop' :/ I managed to run clone desktop both with xinerma and i855crt util, but for some reason it just doesn't work when I want to make these two screens display something else. What happens is that the second LCD connected to the external output displays adjusting for a short while, and then I  get a cloned console on the other screen. Obviously X does not start at all, yet it produces quite a few errors. I'm using x.org built in the breezy badger release. 

Here is my xorg.conf (I've removed the font stuff)

```

Section "ServerFlags"
	Option	"DefaultServerLayout" "Xinerama"
	Option	"Xinerama" "true"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"			"/dev/input/mice"
	Option		"Protocol"			"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"			"/dev/psaux"
	Option		"Protocol"			"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"I855-0"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option   	"DPI" "96 x 96"
	Screen		0
	Option  	"MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
	Identifier	"I855-1"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"DPI" "96 x 96"
	Screen		1
	Option  	"MonitorLayout" "CRT,LFP"
	Option		"DevicePresence" "yes"
EndSection

Section "Monitor"
	Identifier	"MONITOR-0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"MONITOR-1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"I855-0"
	Monitor		"MONITOR-0"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"I855-0"
	Monitor		"MONITOR-1"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Xinerama"
	Screen	0	"Screen0" 0 0
	Screen	1	"Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

And here is what I get from the /var/log/Xorg.0.log

```

(...cut...)
(II) I810(1): CRT: Using hsync range of 30.00-60.00 kHz
(II) I810(1): CRT: Using vrefresh range of 50.00-75.00 Hz
(--) I810(1): Virtual size is 1024x768 (pitch 1024)
(**) I810(1): *Built-in mode "1024x768"
(**) I810(1): *Built-in mode "800x600"
(**) I810(1): *Built-in mode "640x480"
(II) I810(1): Attempting to use 75.08Hz refresh for mode "1024x768" (854)
(II) I810(1): Attempting to use 75.00Hz refresh for mode "800x600" (852)
(II) I810(1): Attempting to use 75.00Hz refresh for mode "640x480" (850)
(++) I810(1): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/X11R6/lib/modules/libfb.a
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/X11R6/lib/modules/libxaa.a
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/X11R6/lib/modules/libramdac.a
(==) I810(1): VBE Restore workaround: enabled.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/X11R6/lib/modules/librac.a
(II) Module rac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after preInit:
	[0] 1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MS[B]
(....)
	[39] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(..cut..)
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
(..cut..)
(II) I810(0): VESA BIOS not detected

*** If unresolved symbols were reported above, they might not
*** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting

```

Anyone encoutered sth like that before ?? I tried to find it on google, and here.. but I didn't try hard enough or there's no answer to this question...

thanks in advance,
high regards

edit:

anyone??

---


---
title: "Cannot Solve Screen Resolution"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2006-02-08
This is my first round with Ubuntu, migrating from WinXP and Mandriva2006. So, I'm totally green. The install went fine except for the screen resolution. I've search the forum and followed a number of suggested solutions including "FixVideoResolutionHowto." Nothing has worked. I have a three-year old system (Dell Dimension, an Envision EN-710e monitor, and an Intel 3D AGP Graphics card. I've reconfigured ...xorg.conf files (several times) with the info I have on the monitor. All I have on the graphics card is the name. The only piece of info that I do not have is the Bus ID. The default is PCI:0:2:0. I left it at that. I'd like to have a resolution of 1024x768 with refresh rates of 30-70kHz horizontal and 50-130 vertical. Screen Resolution Preferences allows only 640x480 @ 85Hz. The xorg.conf file that I read with Nano has all the correct specifications for my system.

Where do I go from here? I'll appreciate any and all suggestions. And I apologize for this long question.
Jerry

---

### Post by Beej on 2006-02-09
Could you post the contents of your xorg.conf?

---

### Post by lakelovers on 2006-02-10
Beej. . . Sorry for the slow reply. Here's the my xorg.conf file:

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
	Load	"GLcore"
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
	Load	"v4l"
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
	Identifier	"Intel 3D AGP Graphics"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"ENVISION"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-130
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel 3D AGP Graphics"
	Monitor		"ENVISION"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
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

---

### Post by infoseeker on 2006-02-10
Here is mine

> SubSection "Display"
	Depth		24
	Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

---

### Post by lakelovers on 2006-02-10
I edited the file conforming with yours, except that I use a depth of 16 and resolutions of "1024x768" and "800x600". I left all the others in the file but commented them with "#" Nothing has changed. I'll try rebooting to see it that resets the selection.

---

### Post by lakelovers on 2006-02-10
That didn't work; It's getting very frustrating. I can't do much with this OS because so many of the windows and type are so large and I can't manuver. There's so much that I like about Ubuntu, it seems that something as critical as screen resolution should not be a problem. Still hoping to find a solution.
Jerry

---


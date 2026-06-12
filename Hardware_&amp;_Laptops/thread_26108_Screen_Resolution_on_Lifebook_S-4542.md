---
title: "Screen Resolution on Lifebook S-4542"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Bjoern on 2005-04-11
Hello,

another tired question for the screen resolution. In Gnome>System>Preferences>Screen Resolution I can only chose 800x600.

Editing /etc/X11/xorg.conf clearly had some effect, at first I could only chose 640x480 if I remember correctly. I even found several people posting their xorg.conf for the S4542 on the web (although I don't know at what time and for which distribution). I copied their entries for the monitor section (which is the one that seems to make a difference), but to no avail. I can't find any values that would give me 1024x768.

What else could I try? In the Configuration Editor there was no "Screen" entry for Gnome, either (I've read about that in another thread).

Many thanks in advance for any help!


Bjoern

---

### Post by whitehat on 2005-04-11
You may want to post your Xorg.conf for examination.  Actually other users had been having issues with monitors defaulting to 640x480 which can be fixed by adding refresh rates to your config, this is one possible solution, you may also want to verify that your display depth has a 1024x768 setting on it.

---

### Post by Bjoern on 2005-04-12
Here is the xorg.conf


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
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
	BusID		"PCI:0:20:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
#	Option		"DPMS"
	HorizSync	20-80
	VertRefresh	20-100	
	ModeLine	"800x600"	36 800 856 960 1056 600 600 605 628
	ModeLine	"1024x768"	75 1024 1032 1156 1328 768 776 778 801	
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		ViewPort	0 0
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Bjoern on 2005-04-12
I just looked at the /var/log/Xorg.0.log and found two lines

"not using 1024x768, not enough memory"

and later

"not using 1024x768, no mode of such name"

(from memory, the actual wording might differ)

---

### Post by Bjoern on 2005-04-12
I have it working with 16bit color depth now, and I suspect that the Fujitsu-Siemens Lifebook S4542 doesn't actually support 24bit color depth at 1024x768. I'll post the working xorg.conf - I think what brought the solution was setting DefaultDepth to 16, however, before that I also added Virtual 1024 768 entries for all modes, and configured the driver to be "vesa" instead of "trident", because I read somewhere that it is faster (I haven't really tried).

xorg.conf ubuntu linux 5.04 Lifebook S4542 :

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
	Identifier	"Trident Microsystems Cyber 9525"
#	Driver		"trident"
	Driver		"vesa"
	BusID		"PCI:0:20:0"
	VideoRam 25600
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	20-80	
	VertRefresh	20-100	
#	ModeLine	"1024x768"	75 1024 1032 1156 1328 768 776 778 801	
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Generic Monitor"
	DefaultDepth	16	
	SubSection "Display"
		Virtual 1024 768
		Depth		1
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Virtual 1024 768
		Depth		4
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Virtual 1024 768
		Depth		8
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Virtual 1024 768
		Depth		15
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Virtual 1024 768
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Virtual 1024 768
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0  "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by murchball on 2008-06-27
I know that that thread is super old, but I just wanted to post that this xorg.conf works fine on Hardy.

---


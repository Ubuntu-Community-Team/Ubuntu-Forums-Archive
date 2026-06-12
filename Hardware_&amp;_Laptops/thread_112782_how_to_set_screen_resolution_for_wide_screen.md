---
title: "how to set screen resolution for wide screen?"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by ctdarksilver on 2006-01-05
as the title above, I am installing kubuntu 5.10 in my dell inspiron 700m, which has a wide screen with resolution 1280*800, in my etc/x11/xorg.conf file it recognized it upon installation, so it contains all the 1280*800 in the screen section, the 1280*800 is the only option and the default option for all the subsection in screen section. however in the control panel it only has the 1024*768 option, how can i config it?

---

### Post by frodon on 2006-01-05
Could you post your xorg.conf file here ?

---

### Post by zonk on 2006-01-05
Hi. 

What graphic card does it have? This could be of some interest.

Greetings.

zonk

---

### Post by Bytebull on 2006-01-05
from your main menu goto /

system/preferences/screen resolution


and you should be able to configure it to fit your laptop.

./ I edited this post...

I use ATI and had the problem trying to configure it with the file until I used the app approch and then was able to get my 1280x800 with no problem.

---

### Post by ctdarksilver on 2006-01-10
My xorg.conf file:
> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-85
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
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
My graphic card is intel extreme integrated
does the information help?

---

### Post by J77 on 2006-01-11
Use 855resolution (from synaptic) to add your desired resolution to those recognised.

I also added something so it changes my res on boot-up - Google for 'ubuntu startupscript'

---

### Post by zonk on 2006-01-12
Hi!

Because you are using an Intel graphic chip you need an new driver for it. The standard driver can't cope with the new hardware. 
Take a look at that web page, there you'll get the driver from and it is explained as well how to use it.

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

Greetings.

zonk

---


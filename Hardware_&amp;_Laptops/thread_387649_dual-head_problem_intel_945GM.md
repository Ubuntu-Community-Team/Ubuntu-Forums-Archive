---
title: "dual-head problem intel 945GM"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by eagletek on 2007-03-18
Hello everybody,

I have a notebook FujitsySiemens AMILO Si 1520,
with a video card:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
(from lspci) 

everything it was working fine, until I needed to configure the dualhead to use an external monitor.
I found on internet how to modify the xorg.conf in order to setup the two monitors and 
this is my xorg.conf file:
[INDENT]
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Screen 		0
	Option	    "VBERestore" "true"
	Option      "DevicePresence" "true"
EndSection


Section "Device"
	Identifier 	"External Video Card"
	Driver 		"i810"
	BusID 		"PCI:0:2:0"
	Screen 		1
	Option		"Display"    "CRT"
	Option 		"MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
EndSection

Section "Monitor"
	Identifier "LCD"
	HorizSync	30-81
	VertRefresh	56-75
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
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

Section "Screen"
	Identifier "LCD-Screen"
	Device "External Video Card"
	Monitor "LCD"
	DefaultDepth 24
	
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen"
	Screen		1 "LCD-Screen" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

[/INDENT]

It is almost correctly working, meaning that i can use both monitor but i have the following problem:
whenever I try to execute openoffice, or xscreensaver 
the current session is closed, X server is restarted and a new login form is shown!
i checked also the /var/log/Xorg.0.log but not errors (EE) are present.
If I use the xorg.conf that I had previously for just single head configuration everything is working fine.. 

any idea? or suggestion?

thanks, 
eagletek

---

### Post by brettr on 2007-03-18
What i did was disable the DRI and GLX modules, that seemed to stop GDM from restarting everytime the screensaver tried to go on. I dont think direct rendering boads well with a dual head set up.

so basically in this section

```
Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

```

change it to look like

```
Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
#Load "dri"
Load "extmod"
Load "freetype"
#Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection
```

and 

```
Section "DRI"
Mode 0666
EndSection
```

to

```
#Section "DRI"
#Mode 0666
#EndSection
```

I am not sure if disabling glx is a must, so you can try it with it on.

I think this should help with the problem

---

### Post by eagletek on 2007-03-18
Thanks a lot!
The problem is solved! :) 

I tried it is not necessary to disable glx module.

bye
eagletek

---


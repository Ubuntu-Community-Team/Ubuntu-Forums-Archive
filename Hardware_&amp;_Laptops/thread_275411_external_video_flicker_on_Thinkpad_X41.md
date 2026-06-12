---
title: "external video flicker on Thinkpad X41"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by howcome on 2006-10-11
I use 6.06 on an IBM Thinkpad X41. I'm very happy, bar two things that happens when I use the external VGA (Fn-F7) port:

 - when both the external VGA and the laptop's monitor are showing, there's a flicker on the external video. Projectors have various sensitivity for the flicker which typically is seen in high-contrast areas. The flicker disappears when I cycle to a mode where the laptop's internal monitor is not showing. This problem is not present in Windows. 

 - sometimes the pointer/cursor disappears when the external monitor is in use. To get it back, I have to cycle through the various modes (Fv-F7) until it returns.

Help is much appreciated. I've been blaming projectors for too long :)

---

### Post by ecoxmit on 2006-10-22
I am also having the same problem. I've tried playing around with xorg.conf with no results. I am posting my xorg.conf file in case anybody has a good idea. 

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
        # FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	#FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/X11/fonts/100dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
        Load    "dbe"
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
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
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
	InputDevice     "cursor" "SendCoreEvents"
   	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
      ###  Option "AIGLX" "true"
EndSection

Section "InputDevice"
     Driver        "wacom"
     Identifier    "cursor"
     Option        "Device"        "/dev/wacom"
     Option        "Type"          "cursor"
     Option        "ForceDevice"   "ISDV4"     
     Option        "Mode"          "Absolute"
   EndSection
   
Section "InputDevice"
     Driver        "wacom"
     Identifier    "stylus"
     Option        "Device"        "/dev/wacom"
     Option        "Type"          "stylus"
     Option        "ForceDevice"   "ISDV4"
EndSection
   
Section "InputDevice"
     Driver        "wacom"
     Identifier    "eraser"
     Option        "Device"        "/dev/wacom"
     Option        "Type"          "eraser"
     Option        "ForceDevice"   "ISDV4"
EndSection

 Section "DRI"
	Mode	0666
 EndSection

# Removes ctrl-alt-backspace
 Section "ServerFlags"
 	Option		"DontZap"		"yes"
 EndSection

```

---

### Post by baffle on 2006-10-29
> **howcome said:**
> I use 6.06 on an IBM Thinkpad X41. I'm very happy, bar two things that happens when I use the external VGA (Fn-F7) port:

 - when both the external VGA and the laptop's monitor are showing, there's a flicker on the external video. Projectors have various sensitivity for the flicker which typically is seen in high-contrast areas. The flicker disappears when I cycle to a mode where the laptop's internal monitor is not showing.

The same problem was in Breey and now in Edgy. I have a T42 with an ATI Technologies Inc Radeon Mobility M7 LW running the opensource ATI drivers.

Sorry for the "me too", but it is quite annoying. :-)

---

### Post by howcome on 2006-12-10
> **howcome said:**
>  - when both the external VGA and the laptop's monitor are showing, there's a flicker on the external video. Projectors have various sensitivity for the flicker which typically is seen in high-contrast areas. The flicker disappears when I cycle to a mode where the laptop's internal monitor is not showing. This problem is not present in Windows. 


It seems that the flickering can be removed by adding this into xorg.conf:

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option          "MonitorLayout" "CRT,LFP"
	Option          "Clone" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync    31.5-90
	VertRefresh  50-90
EndSection

---

### Post by ecoxmit on 2006-12-11
> **howcome said:**
> It seems that the flickering can be removed by adding this into xorg.conf:

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option          "MonitorLayout" "CRT,LFP"
	Option          "Clone" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync    31.5-90
	VertRefresh  50-90
EndSection
That didn't work for me :(

---


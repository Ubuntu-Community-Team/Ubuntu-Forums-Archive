---
title: "Using VGA OUT in laptops"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by Chillout on 2005-10-07
Hello.

I've been searching through the forums and I can only find guides on how to use X in a computer with 2 graphic cards. I would like to know how what is the standard configuration changes to configure the display of the VGA OUT in a laptop.
If I don't do anything, when I connect to a monitor, I can get picture in the monitor as well as in the laptop's LCD. The problem is that the monitor is showing my 1280x800 desktop in a 640x480 resolution! I have to scroll around to see the rest of the screen.
I tried to create another "Screen" section in xorg.conf, but to no avail. Also tried to use the Option "Clone" with the same result. Can anyone help?

---

### Post by John.Michael.Kane on 2005-10-07
You will need to post system spec's

---

### Post by Chillout on 2005-10-07
[QUOTE=SD-Plissken]You will need to post system spec's[/QUOTE]

Oops... sorry :|

I have a Acer Aspire 1692WLMi with a x700 ati graphic card, running Breezy and the default ati drivers (I'm not using the ones from ATI because I can't get them to go higher than 1024x768).

Here is my xorg.conf

```

Section "Files"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	64000
#	Option		"UseFBDev"		"true"
	Option "MonitorLayout" "LVDS,CRT"
#	Option "CloneMode" "On"
#	Option "CloneMode" "1024x768"
#	Option "VideoOverlay" "on"
#	Option "UseInternalAGPGART" "no"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
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

```

Hope this helps.

---

### Post by John.Michael.Kane on 2005-10-07
There have been some issues with ati driver's. at most i can tell is for you to have a look at the howto's for ati drivers.

[http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati)
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)
[http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)


i hope it helps.

---

### Post by Chillout on 2005-10-07
Thanks for all the help.
With the real ATI drivers I can get the VGA OUT to work properly, although I still suffer  from the "no more than 1024x768" issue. I guess that I will change drivers just before the presentations... :|

---


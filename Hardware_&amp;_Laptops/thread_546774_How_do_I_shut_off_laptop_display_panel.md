---
title: "How do I shut off laptop display panel?"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by mhenry35 on 2007-09-09
I just got a nice 22" widescreen monitor that I am hooking up to my Gateway MT6070 laptop, and there is a display issue, where when I switch to 1680x1050 mode, my system makes the switch, but the video doesn't take up the whole screen.

The resolution is available, but I think the problem is that since the system leaves the laptop display panel turned on, I think it's causing a horizontal sync issue on the big monitor.

I've turned off the laptop panel in the BIOS, and it seems to work great, but when Gnome desktop loads, it turns back on again.  I've updated the xorg.conf with the correct sync info for my monitor, and nothing seems to help.  I really think the key is getting the laptop display panel to stay off when I'm using the external monitor, but that's just a theory.

Here is a copy of my xorg.conf:


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel 945GM"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Envision G218A1"
	Option		"VESA"
	HorizSync	30-80
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"Laptop Panel"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel 945GM"
	Monitor		"Envision G218A1"
        Monitor         "Laptop Panel"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by frith on 2007-09-09
Okay, I'm not a super expert, but I'll ask the obvious question: Are you booting the laptop with the monitor plugged in? On my toshiba m200 I need to boot with the monitor plugged in for it to work correctly.

Other than that, since you are using an ATI card, I don't think I'll be much help :)

---

### Post by mhenry35 on 2007-09-10
Yes, I'm booting with the external monitor plugged in.  The video looks great until Gnome Desktop loads (and it reactivates the laptop display.)  

The other odd thing is that the function key to switch between displays also doesn't work.

---

### Post by mhenry35 on 2007-09-18
Still don't know the real answer, but uninstalling the new intel driver fixed this part of the problem.  Now I have to use 915resolution to set the resolution, but at least the laptop panel stays off now.

I still can't use the function key to switch screens, though.

---

### Post by Linicks on 2007-09-18
Unfortunately, there seems to be a few issues with Intel driver[s] at the mo.  I have had similar issues:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133568](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133568)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110379](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110379)

Nick

---


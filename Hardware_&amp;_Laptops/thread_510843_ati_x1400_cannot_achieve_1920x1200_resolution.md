---
title: "ati x1400 cannot achieve 1920x1200 resolution"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by aum11 on 2007-07-27
Dell 9400 with ati x1400 and 17" uxga screen 1920x1200.

Have tried so many howtos on the forum and still it is stuck at 1280x1024 resolution.

Any help would be so gratefully received.

Thanks

---

### Post by myk.dinis on 2007-07-27
Post your /etc/X11/xorg.conf and /var/log/Xorg.0.log and I'll troubleshoot you real quick...

open a terminal and type   sudo cat /etc/X11/xorg.conf > xorg.txt
then type   sudo cat /var/log/Xorg.0.log > log.txt

then open thos (they'll be on your deskto) and cut n paste the contents here...


Cheers!

---

### Post by aum11 on 2007-07-27
Thanks for Your help myk.dinis.

The commands put nothing on the desktop.

I have left of the log as it is so large.  Let me know if You need it, or perhaps a change in command.

Here is standard output from gedit for xorg.conf:

Section "Module"
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
	Identifier	"ATI Mobility Radeon x1400 256MB"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Mobility Radeon x1400 256MB"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

### Post by fredj on 2007-07-28
Make a backup copy of xorg.conf. Open a terminal the type cd /etc/X11 and then type
sudo cp xorg.conf xorg.conf.save.
Then type sudo gedit xorg.conf to edit the file. Look at all the Modes lines. Add "1920x1200" (and a 
space) at the beginning of all of these lines after the word Modes. Then save the file and restart and
see if you can select the correct resolution.

---

### Post by aum11 on 2007-07-28
Thanks Fredj for your response.

I have tried this several times with always the same result:

it starts to generate the desktop and then fails and reverts to black and white screen and then retries and fails again.  Eventually it reverts to 1280x1024 resolution and the 1920x1200 resolution is no longer an option.

Suggestions?  I REALLY need some help with this.

---

### Post by aum11 on 2007-08-02
Resolved by reinstalling.  My full response is here: [http://ubuntuforums.org/showthread.php?t=508433&page=2](http://ubuntuforums.org/showthread.php?t=508433&page=2)

---


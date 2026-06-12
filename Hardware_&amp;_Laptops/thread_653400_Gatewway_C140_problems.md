---
title: "Gatewway C140 problems"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by Wamoc on 2007-12-29
Ok, I recently installed linux on my Gateway C140 tablet. I have gotten most hardware to work (the only thing not working is the fingerprint reader, which is fine; i had it working before, but it killed all other functionality).  

My stylus is working, but I can't get it calibrated.  I have tried various directions in other threads, but none have worked (I tried the directions on a site in German, it didn't recognize me using the stylus for that program).  It uses a Wacom device for the stylus.
Also, I haven't been able to get the keycodes for the buttons on the screen part (with windows it rotated the screen, etc). I have also tried other threads for directions with this.

If anyone could help with this, it would be greatly appreciated.

---

### Post by raghav_p on 2008-01-10
I have a C140 as well.

The fingerprint reader is the same as the ones in Thinkpads, thus the thinkfinger package works; there are known issues with various gnome utilities, so I have decided to hold off on using that.

My pen seems to be calibrated fairly well, so I don't have that problem.

As for the buttons on the tablet screen, they use some sort of ACPI stuff in a device called MSTabletButtons (/sys/devices/acpi_system:00/device:00/PNP0A08:00/MSTabletP:00) but I can't find any module that supports it.

Does anybody have any thoughts?

---

### Post by KingArthur10 on 2008-01-21
You mention the fingerprint reader problems.  I've recently purchased a c140 and am curious as to whether or not the fingerprint reader works and if so, what problems it has.  Also, I can't seem to get the built-in pen's right-click button to work as a right click.  Any ideas?

---

### Post by teval on 2008-01-23
Hi,

Can you tell us how you got the tablet to work?
I've tried but for some reason I can't get it to work at all.


Thanks

---

### Post by KingArthur10 on 2008-01-23
> **teval said:**
> Hi,

Can you tell us how you got the tablet to work?
I've tried but for some reason I can't get it to work at all.


Thanks

To get the tablet functionality to work, you need to edit your xorg file.  To do so, you need to open a terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

You need to uncomment the following lines under Section Server Layout:

```
		InputDevice     "stylus"	"SendCoreEvents"
		InputDevice     "cursor"	"SendCoreEvents"
		InputDevice     "eraser"	"SendCoreEvents"

```

Also, I adjusted a couple of other values.  I'll just post my xorg file here so you can pick and choose what helps you.

```
Section "Files"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
#	Option		"SHMConfig"	"True"
        Option          "MaxTapTime"            "0"
	Option		"RightEdge"	"5820"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"PressCurve"	"50,0,100,50"	# Custom preference
	Option		"Button1"	"1"
	Option		"Button2"	"3"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"RandRRotation"	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
		InputDevice     "stylus"	"SendCoreEvents"
		InputDevice     "cursor"	"SendCoreEvents"
		InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

An explanation of some of the values I've altered: under the synaptic touchpad, the value "maxtaptime" set to zero disables tapping.   The "rightedge" value corrects the double-wide scroll area.  
```
	Option		"PressCurve"	"50,0,100,50"	# Custom preference
```
That one makes it so that you have to press harder for darker shades.  The default pressure curve was too light.

```
	Option		"Button2"	"3"
```
That one makes it so that pressing the pen button and tapping the screen enables right-click.

If you have any other questions, let me know.  Send me a PM or an email if I don't respond within a day.

---


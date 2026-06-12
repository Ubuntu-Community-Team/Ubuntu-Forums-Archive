---
title: "Samsung 203B 1400X1050 Not Working Feisty or Gutsy"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by genxian on 2007-08-25
Hello everyone,

I have a Samsung SyncMaster 203B.  It's native resolution is 1400x1050.  I have a ATI Radeon 9000 graphics card.  I am using an NFORCE2 chipset motherboard.

I am having trouble getting my monitor to run 1400x1050 resolution regardless of using Feisty 7.04 or Gutsy 7.10 Tribe 5.  Right now when I go to my "Screen Resolution Preference" I can select 1400x1050.  The refresh rates are a weird  379HZ, 302HZ, 303HZ, 429HZ.  These are obviously weird to me.

If I select 1400x1050 resolution the result is the screen is to tall (I lose the bottom panel, and the entire screen is shifted to the right about 3 inches.  I can't correct this issue using the monitors built-in adjustments.

Another weird thing is that is I leave the monitor in 1400x1050 and restart X using Ctrl Alt Backspace the login page for Ubuntu looks perfect!  But as soon as I login the screen gets too tall and shifts to the right.  I will include my xorg.conf below.  Any help you all can provide would be greatly appreciated.  ALSO, this monitor runs perfectly fine in Windows.

Finally, the current xorg.conf I am including below is the result of running dpkg-reconfigure xserver-xorg.

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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
EndSection
```

---

### Post by genxian on 2007-08-26
I'm wondering if this monitor is supported at all.  In the lower resolutions which I am forced to use the fonts are all blurry it just is a mess.  Hopefully I can get this resolved soon.  Thanks for any help you all have.

---

### Post by oh6eh on 2007-09-06
Hi!

I just wrote a description to solve this problem, see

[http://ubuntuforums.org/showthread.php?p=3318820#post3318820](http://ubuntuforums.org/showthread.php?p=3318820#post3318820)

Cheers,

Kaj

---

### Post by haelters on 2008-01-21
based on the solution of oh6eh, I've found another one using the intel driver, which also allows XRandR: [http://ubuntuforums.org/showthread.php?p=4180275#post4180275](http://ubuntuforums.org/showthread.php?p=4180275#post4180275)

---


---
title: "Touchpad after suspend"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by Sugz on 2008-02-01
Help.
Whenever i use Suspend on Gutsy, the touchpad and buttons associated with it do not work. 
is there a fix for this problem?
-Sugz

---

### Post by Sugz on 2008-02-02
Anyone?

---

### Post by Sugz on 2008-02-02
im sorry to keep on harping on about this problem. But what with ubuntu being my primary OS on my laptop, i need this feature as not all of my lecture theatres have a power socket :(

But any help will be greatly appreciated

-Sugz

---

### Post by Sugz on 2008-02-03
At the end of another unsucesfull day tring to fix this problem.
Here is some info.

Ubuntu Version: 7.10 Gutsy
Kernel: 2.6.22-14 generic

Contents of Gconf file.

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Option		"HorizEdgeScroll"	"0"
	Option 		"SHMConfig"		"on"
	Option          "HorizScrollDelta"      "0"
	Option 		"SHMConfig"		"on"
	Option		"VertEdgeScroll"	"0"
	Option		"VertTwoFingerScroll"	"0"
	Option		"HorizTwoFingerScroll"	"0"
	Option		"RTCornerButton"	"0"
	Option 		"RBCornerButton"	"0"
	Option		"Tapbutton2"		"3"
	Option		"Tapbutton3"		"2"
	Option 		"FingerLow"		"10"
	Option		"FingerHigh"		"20"
	Option		"MaxTapTime"		"180"
	Option		"VertScrollDelta"	"20"	
	Option 		"HorizScrollDelta"	"50"
	Option		"CircularScrolling"	"on"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```




once Again any help appreciated
-Sugz

---

### Post by drorata on 2008-02-16
I'm having the same problem. I'm using Lenovo 3000 N100 with Kubuntu 7.10

Once the system resumes from suspension the touchpad is dead. I don't know if it is connected or not, but the NUMLOCK is turned on after the suspension as well.

Any tips? Ideas? It seems like it is a well known problem...

---

### Post by drorata on 2008-02-16
Seems like I found the solution for my case. Refer to:

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768)

Under the "Sleep" section you'll find the instructions. I followed them and now the touchpad perfectly!

In a nut shell, add to:
/boot/grub/menu.lst the following tag "i8042.reset" under #defoptions

Hope you can find it useful.

Have a great weekend,
Dror

---

### Post by Sugz on 2008-02-17
Thanks for the link, unfortunately the "fix" does not work.. :confused:

---


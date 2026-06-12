---
title: "PS/2 Mouse and Synaptics Touchpad"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by GepettoBR on 2008-02-15
I have a Compaq laptop, dual-booting XP and Gutsy. The touchpad works great under Gutsy (and is much less shaky with high sensitivity settings than in Windows) but I prefer using the mouse for more delicate operations, like path editing in the GIMP. Having only two USB ports, I use a PS/2 mouse. Under Windows, if I plug in the mouse the touchpad is disabled and the mouse enabled. In Gutsy, the mouse lights up but doesn't work and the touchpad is still functional. Both the touchpad and the mouse are listed in xorg.conf (and in case it makes any difference, the mouse comes first). Is there a way to get the same detect-and-switch function as in XP?

---

### Post by agim on 2008-02-15
I would start by posting your xorg.conf file. I don't know how to answer your problem, but someone here will probably ask to see that file. So I thought I'd help you get that out of the way.

---

### Post by GepettoBR on 2008-02-16
> **agim said:**
> I would start by posting your xorg.conf file. I don't know how to answer your problem, but someone here will probably ask to see that file. So I thought I'd help you get that out of the way.

Alright, here's my full /etc/X11/xorg.conf file: ```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option 		"SHMConfig" 		"true"
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
	Identifier	"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
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

---

### Post by james9876 on 2008-02-16
I'm similar, but i use a usb mouse, the only difference is that it automatically dectects the usb mouse so i can use it automatically.

Have you tried gsynaptics via synaptic package manager.  that allows you to disable the touchpad, does the mouse work then?  If not, you may have to turn the touchpad back on with the keyboard controls.  Hope that's of help?

---

### Post by GepettoBR on 2008-02-17
Hi, thanks for the reply. Using gsynaptics to disable the touchpad also didn't work. I can't get the mouse to function at all.

---

### Post by james9876 on 2008-02-17
Sorry I can't help anymore further then, :(.  I don't have a ps/2 mouse to play with :S.  The only other solution perhaps is a usb hub, and use a ps/2 usb converter for the mouse maybe?  That unfortunately isn't ideal for a laptop :(.

---

### Post by GepettoBR on 2008-02-18
Bump. No one else?

---


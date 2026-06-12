---
title: "Intel GMA 950"
date: 2008-07-07
forum: Hardware
---

### Post by sn0m on 2008-07-07
Hi guys, i bought a new laptop, hp with intel GMA 950 build in graphic card.
It is said that intel generally supports linux, has any of you had any experience with the above card?
Kind regards
Sokol

---

### Post by overdrank on 2008-07-07
> **sn0m said:**
> Hi guys, i bought a new laptop, hp with intel GMA 950 build in grphic display.
It is sai that intele generally supports linux, has any of you had any experience with the above card?
Kind regards
Sokol

Hi and I have the intel 945 chipset on my laptop and works fine on Gutsy.  :)

---

### Post by stchman on 2008-07-07
> **sn0m said:**
> Hi guys, i bought a new laptop, hp with intel GMA 950 build in graphic card.
It is said that intel generally supports linux, has any of you had any experience with the above card?
Kind regards
Sokol

That card will work OOB with Compiz.  I have the x3100 and it works great.

---

### Post by WhizCas on 2008-07-23
> **overdrank said:**
> Hi and I have the intel 945 chipset on my laptop and works fine on Gutsy.  :)
Hi, can you maybe post your xorg.conf?

---

### Post by overdrank on 2008-07-23
> **WhizCas said:**
> Hi, can you maybe post your xorg.conf?

Sure :)
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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

---

### Post by grantek on 2008-07-23
Yep, I have a GMA 965 in a laptop and it works great for compiz out of the box :)
Only issue I had was enabling compiz with an external monitor attached, you need to arrange your screens so that your full desktop fits in a 2048x2048 box (this is a hardware limitation), and add a "Virtual" line in the "Display" subsection of your xorg.conf. A bit of googling should help if you ever need to run dual monitors.

---

### Post by WhizCas on 2008-07-24
I've bought the Medion akoya, almost the same as the MSI Wind. When I want to start X i get this message, I used the same Xorg.conf as above:

(EE) [drm] drmOpen failed.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 7932 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Tiled allocation failed.
(WW) intel(0): Couldn't allocate tiled memory, fb compression disabled
(II) intel(0): Attempting memory allocation with untiled buffers.
(WW) intel(0): Failed to allocate EXA offscreen memory.
(II) intel(0): Untiled allocation failed.
(EE) intel(0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0

Any idea what it could be?

---


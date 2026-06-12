---
title: "Wacom Penpartner generating random clicks"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by gwi on 2006-09-11
I have a Wacom Penpartner, which seems to generate random click events whenever I move the stylus around. For example I have an icon on the panel that starts Firefox. When I move the stylus to get the mouse pointer over the Firefox icon, the moment it reaches the icon Firefox gets started a dozen times, before I even get a chance to push the stylus down onto the tablet.
When moving over an empty desktop I sometimes see a selection rectangle, indicating the stylus touching the tabet. But it isn't.

The computer has a multi-boot setup. When booting Windows XP, everything works as it should. The problem only occurs in Ubuntu (version 2.6.15-26-686).

The Penpartner is directly connected to the USB port of the computer. The keyboard and a mouse (both PS2) are connected via a KVM-switch (Avocent Switchview), because the are also needed on another computer.

Here is a part of my xorg.conf:
```
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Mode"		"absolute"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice     "stylus"    "SendCoreEvents"
EndSection

```

The problem doesn't always show, but I think it is related to the KVM-switch. Any ideas what could be the cause of the problem, and how to solve it?

---

### Post by gwi on 2006-11-29
Well, it's been some time. The computer is no longer multi boot, just Ubuntu 6.06 LTS (kernel 2.6.15-27-686).
The KVM can be ruled out. The problem also appears when the PenPartner is connected directly to the computer.

Any ideas this time how to solve the problem?

---


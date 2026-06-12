---
title: "Microsoft Wireless Optical Mouse (2.0A/Model 1008) Tilt Wheel Doesn't Work"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by DaneM on 2007-10-27
The mouse (mentioned in the title) works perfectly, but it doesn't scroll horizontally with the tilt wheel.   If I "sudo cat /dev/input/event4", and use the mouse tilt function, I get the expected garbled output, indicating that it's at least sending a signal when I do so.

Below are some Xorg.conf configurations I've tried.  The first one is the Ubuntu (Gutsy) default.  The one without "#" in front of every line is the one I'm using now, but none of them have worked so far.

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"evdev"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/event4"
#	Option		"SendCoreEvents"	"true"
#	Option		"Buttons"	"9"
#	Option		"evBits"	"7"
#	Option		"keyBits"	"1f"
#	Option		"relBits"	"+1 +4 +3
#	Option		"Pass"		"3"
#	Option		"ZAxisMapping"	"4 5 7 6"
#EndSection

#Section "InputDevice"
#Identifier "Configured Mouse"
#Driver "evdev"
#Option "Device" "/dev/input/event4"
#Option "CorePointer"
#EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5 7 6"
Option "Emulate3Buttons" "false"
Option "Buttons" "9"
Option "ButtonMapping" "1 2 3 4 5 6 7 8 9"
EndSection

Thanks for any help you can provide!

--Dane

---


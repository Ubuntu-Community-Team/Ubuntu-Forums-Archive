---
title: "Touchpad (Alps) and Scrolling"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by apu95 on 2005-05-10
Ok, so I installed Hoary on a HP Pavilion DV4030CA (see sig). The touchpad works great, the speed of the arrow is good and I can tap the pad to represent a click. I'm trying to get the right side of the pad (which has these ridges) to work as a vertical scroll section. I tried a method that was listed to configure a Synaptics pad in Warty (which apparently was supposed to work for Alps), but all it did was not let me boot into X. 

this is my xorg.conf section for inputs:
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
------------------------

and this is the final part:
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
-----------------------
any ideas on how i can enable it?


thx :)
Apu

---

### Post by tjabri on 2005-05-11
Yeah I'm having the same problem. Alps touchpad doesn't work on Ubuntu, but it works on Suse 9.3. I'm gonna try to see what the config for Suse is and maybe apply that code towards Ubuntu.

---

### Post by dejitarob on 2005-05-19
[http://ubuntuforums.org/showthread.php?t=28132](http://ubuntuforums.org/showthread.php?t=28132)
You will need to apply a kernel patch since Hoary uses 2.6.10 and the linux kernel doesn't support ALPS until 2.6.11. There is 2.6.11 in the Hoary repository but its an outdated, unstable version. I'm planning on just compiling the 2.6.11 and adding some patches myself, like the [ck performance patch set](http://members.optusnet.com.au/ckolivas/kernel/).

---


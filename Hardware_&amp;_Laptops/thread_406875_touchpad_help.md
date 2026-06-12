---
title: "touchpad help"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by jputman01 on 2007-04-11
hey guys,

some more help would be appreciated!! im using feisty on hp dv6000, my touchpad was working just fine, the scrolling worked and everything. Then I did two things and one of them changed something. I got my video card working (nvidia) and pluged in a usb mouse (just to see if it worked). I restarted X to make sure my video card changes worked and now my mouse is different. The scrolling on the pad no longer works, the sensativity is different too. I did some searching and saw where people were posting their xorg.conf files and they said something to the effect of:

device:    "synaptic touch pad"
driver:     "synaptic"

mine is different now and unfortunately I didn't look at it before, mine says:

device:     "mouse0" and it has a different driver listed (sorry im not on my laptop right now to paste the actual file but I can later)
I tried to gsnyaptics but it says I need to add "SHMConfig" "true" to my xorg.conf file which I did and it still gives me that error when I try to open gsynaptics.

how to i get my old toughpad settings back where I can scroll and stuff? can i simply change my xorg.conf to "synaptic touch pad" and "synaptic" driver? and help would be great.

---

### Post by MyR on 2007-04-12
a temporary solution may be to unplug the usb mouse when you boot up. I had this problem under breezy and was able to solve it but now everything works great on edgy

heres my xorg.conf if it helps
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

---

### Post by jputman01 on 2007-04-12
im sorry, i should have explained better. i dont currently have the usb mouse plugged in, i just had it plugged in that one time to see if it would work. it is currently unplugged.

the weird thing is my xorg.conf has the section for input device "configured mouse" but doesnt have the second section that says input device "synaptic touchpad." i dont have both sections just the first one.

is that something i can just add in??

---

### Post by MyR on 2007-04-12
I'd say it's worth a try. make sure you back up your xorg.conf firsth though.

---


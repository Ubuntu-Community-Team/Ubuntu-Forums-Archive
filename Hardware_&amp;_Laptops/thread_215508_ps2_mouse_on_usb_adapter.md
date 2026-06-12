---
title: "ps/2 mouse on usb adapter"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by Alasiac on 2006-07-14
Hi all,

I've searched this forum for a while (and did some googling) but haven't found an answer yet on this:

I have a ps/2 mouse attached to my laptop with an usb adapter, but it doesn't give any sign of life. When plugging in my adapter, I can see the adapter in my device manager, I find an extra event in /dev/input but still nothing happens. Is there anything I can check what's happening to my events, where they end up or where I need to look for more information? I've included some info below my message.

Thanks for every hint,

Kind Regards,
Alasiac

These are my profiles:
Hardware: Fujitsu Siemens LifeBook with usb-adapter from hp, simple mouse attached

Device Manager has this driver under USB UHCI #1 when mouse attached:
ps/2 adapter v1.13
>USB HID interface
>> Y.G.I By [email]kunichen@ms8.url.com.tw[/email] PS/2 Adapter V1.13
>USB HID interface
>USB Raw Device access

xorg.conf (the part I think is relevant here):
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
...
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Alasiac on 2006-07-16
Ok, I think I know the problem: the ps/2 to usb adapter I have has two ports: keyboard and mouse. When looking at my devices with cat /proc/bus/input/devices I see that one device is added as ps/2 adapter with a keyboard handler. There obviously something wrong here, but I don't know yet how to fix it.

---


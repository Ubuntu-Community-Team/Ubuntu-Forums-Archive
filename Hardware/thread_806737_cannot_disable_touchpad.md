---
title: "cannot disable touchpad"
date: 2008-05-25
forum: Hardware
---

### Post by LianerGoist on 2008-05-25
Hi

I have tried to disable the touchpad following the describtion here:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Well, it say the same as most other sites on the internet - add

Option          "SHMConfig"             "on"

to /etc/X11/xorg.conf. But it doesn't work. After reboot I get an error saying 

"Can't access shared memory area. SHMConfig disabled?"

when I run "synclient TouchpadOff=1".


I have also tried to comment out (#) the entire touchpad section in xorg.conf, but it changed nothing. The touchpad is still working, and no errors. Does that kind of indicate xorg.conf is not even read? Or...?

I found a program called tpconfig. It says

thomas@zepto:~$ sudo tpconfig -D
Probing mouse port [/dev/psaux]
Grabbing mouse port [/dev/psaux]
Trying Synaptics detection.
[query 00 => 0x60 0x3 0xc8]
Found Synaptics Touchpad.
[query 0x3 => 0x60 0x3 0xc8]
Firmware: 8.96 (multiple-byte mode).

So? The tp is a Synaptics Touchpad, the mouse port is the same I use in xorg.conf, ... 

What can I do to narrow down the problem?

Thomas


```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option          "SHMConfig"             "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---


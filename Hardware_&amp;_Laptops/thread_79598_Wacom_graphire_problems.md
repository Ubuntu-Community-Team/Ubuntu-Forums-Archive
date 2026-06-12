---
title: "Wacom graphire problems"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by arubin on 2005-10-20
Trying to set up my wacom graphire with kubuntu. I have done this successfully with slackware so I have a little experience. 

My problems are that the wheel on the wacom mouse does not work. (It does work on my ps2 mouse).
Also GIMP does recognise that there is a stylus, cursor and eraser and at first recognises them changing but after changing one to the other they do not work and eventually none of the pointers work, forcing ctrl-alt-back 

xorg reads

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
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/event2"
	Option "Mode" "relative"
        Option "Type" "cursor"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/event2"
        Option "Type" "stylus"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/event2"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection

I have tried making wacom.o but so far am unsuccessful. Now getting this error

***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built

Thanks for any help:mad:

---

### Post by arubin on 2005-10-20
The answer is:
change
	Option		"Device"		"/dev/input/mice"

to

	Option		"Device"		"/dev/input/mouse0"

---


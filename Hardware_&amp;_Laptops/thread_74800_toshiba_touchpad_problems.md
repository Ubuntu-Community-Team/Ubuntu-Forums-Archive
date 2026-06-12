---
title: "toshiba touchpad problems"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by karmon on 2005-10-12
hello, i tried following this howto on the forums to get the touchpad working, but i couldnt find the file i was suppose to edit (by the way, im using ubuntu 5.04), so i really need help getting my touchpad to work, thank you.

EDIT: my touchpad works in ubuntu live, just thought you should know that.

---

### Post by Technoviking on 2005-10-12
It is in your /etc/X11/xorg.conf

Here is my mouse section. I can use both a USB mouse and my touchpad
```
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
```

Mike

---

### Post by karmon on 2005-10-12
thats what is already there.

---

### Post by Technoviking on 2005-10-13
[QUOTE=karmon]thats what is already there.[/QUOTE]
Check your X.log file to see if the synaptic driver is loading.

---


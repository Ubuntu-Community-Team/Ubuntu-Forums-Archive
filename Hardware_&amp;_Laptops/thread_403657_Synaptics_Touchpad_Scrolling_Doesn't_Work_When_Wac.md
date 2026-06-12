---
title: "Synaptics Touchpad Scrolling Doesn't Work When Wacom Graphire 4 Plugged in"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by niiiick on 2007-04-07
Using Edgy, the synaptics touchpad's vertical scrolling capability stops working when a wacom graphic tablet is plugged in.  Following is my xorg.conf:


```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option	"USB"		"on"
  Option	"PressCurve"	"50,0,100,50"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option	"USB"		"on"
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option	"Mode"		"relative"
  Option	"USB"		"on"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

```

i've tried adding Option "VertEdgeScroll" "1" to the touchpad section, but nothing.  any ideas?

---

### Post by niiiick on 2007-04-07
hmm... after i restarted randomly it seems to work.  this doesnt always fix the case though... why would it work sometimes and not always?

---

### Post by frafu on 2007-04-08
Hello, 

The Accessibility Forum is intended for discussions about software to enable and to simplify the access to the computer for disabled people. So, I am moving this thread to the Hardware & Laptop forum, where it might have a better chance to get replies. 

Have a nice day. 

Francesco

---

### Post by rynix on 2007-04-25
I am having the same issue has anyone solved this yet ?

---


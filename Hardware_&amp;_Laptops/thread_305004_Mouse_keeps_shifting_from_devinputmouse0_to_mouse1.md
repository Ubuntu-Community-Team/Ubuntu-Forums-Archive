---
title: "Mouse keeps shifting from /dev/input/mouse0 to mouse1"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by finferflu on 2006-11-22
Hi all,
I'm having this kind of problem since July, but now it's really starting to stress me.

In order to make my mouse, touchpad and pen tablet work together at the same time, I had to rearrange my xorg configuration in the following way (I'm reporting only the relevant bit):

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "SendCoreEvents"        "true"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "auto-dev"
       Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event4"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event4"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "CorePointer"
	InputDevice	"Synaptics Touchpad" "AlwaysCore"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

In this way everything works fine, except for one thing (let's say two): most of the time when I reboot my machine, the mouse is dead, because in xorg it's configured as /dev/input/mouse0, whereas in the current session it's on /dev/input/mouse1, and vice-versa when I set it up the other way round. Is there any way I can prevent this happening? (Sorry for my lack of technical terminology, but I'm not really experienced).
Apart from this, the other minor problem is that everytime I plug my pen tablet in, I need to restart my session in order for it to be recognised. It's not really "Plug & Play". I can cope with that, but I was wondering whether there was a better solution.

Thanks a lot for your time!

---

### Post by chris_c28 on 2006-12-05
Exact same problem here. Does anyone have any idea on why this is the case? It only happens to me on 6.10, while it works fine in 6.06.

---

### Post by finferflu on 2006-12-05
Have you modified your xorg.conf like I did? Because I think I've solved my problem by installing wacom-tools and leaving the mouse under the device /dev/input/mice. My touchpad and pen tablet are respectively under /dev/input/psaux and /dev/input/wacom.

---

### Post by chris_c28 on 2006-12-05
I've tried various ways, but managed to see that it only works after I log in and out of a gnome session.

---


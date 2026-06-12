---
title: "How do you get Touchpad, USB mouse and Pen Tablet all working at the same time?"
date: 2006-07-23
forum: Hardware &amp; Laptops
---

### Post by finferflu on 2006-07-23
Hi,

I have just configured my Wacom Volito 2 to work properly (i.e. with pressure sensitivity and absolute positioning) following an how-to on this forum ([http://www.ubuntuforums.org/showthread.php?t=25151)](http://www.ubuntuforums.org/showthread.php?t=25151)). 

But I have just discovered that my touchpad is no longer working. I know the cause of the problem. In fact, following the how-to, I have set in xorg.conf to recognise /dev/input/mouse0 as the Configured Mouse, the "CorePointer", while my touchpad is on /dev/input/mouse1. 

My question is how do I get all of them working together simultaneosly?
I have tried this, but I am not really experienced, and in fact I am not surprised it is not working: 
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
	Identifier	"Touchpad"
	Driver		"mouse"
	Option		"SendCoreEvents"
	Option		"Device"		"/dev/input/mouse1"
	Option		"Protocol"		"auto"
	Option		"ZAxisMapping"		"4 5"
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
	InputDevice	"Touchpad" "SendCoreEvents"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
EndSection
```

With this configuration the touchpad and the usb mouse are working, but the pen tablet is dead. I guess it's an obvious result for putting the touchpad and the pen tablet sending core events. I don't know any other alternative option to enable the touchpad to coexist with the pen tablet.

Thanks for your time.

---

### Post by finferflu on 2006-07-25
By the way, I am also having new troubles:

Everytime I start up Ubuntu, I get the touchpad working and the mouse is dead. So I have to edit xorg.conf every time and change the input of the "Configured Mouse" from /dev/input/mouse0 to /dev/input/mouse1 and vice versa. 
When the mouse input was set to mouse0 before shutting down, at the next start up mouse0 is the touchpad. It seems the touchpad gets over the mouse to become the "Configured Mouse".

It's not that big deal, because it takes less than a minute to edit xorg.conf, but it's getting annoying.

Thanks again for your time.

---

### Post by finferflu on 2006-07-25
Ok, I am now replying to myself, I've almost sorted it all out. These are my relevant sections in xorg.conf, and I must say that now my touchpad works better than it used to do on Windows:

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

The only problem is that, in order to use the pen tablet I have to restart the session with it plugged in, otherwise it's dead. I don't know if there is a solution for that, but restarting a session is better than editing xorg.conf everytime AND restarting the session :) 

I hope this will come handy to somebody else, even though it is not perfect.

---


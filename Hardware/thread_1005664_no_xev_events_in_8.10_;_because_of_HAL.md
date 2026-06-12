---
title: "no xev events in 8.10 ; because of HAL?"
date: 2008-12-08
forum: Hardware
---

### Post by royalCS on 2008-12-08
Hi,
short version: 
-hp tc4400 (tablet pc)
-no xev events for tablet keys / express keys /quicklaunch buttons (whatever you like to call them)
-no xev events for some multimedia keys (presentation and information/help)

**but:** 
I remember I got some events with a former version of ubuntu, and these multimedia keys where working out of the box. 
--> Tried an old live CD. I got xev-events for the multimedia keys with my 6.10 live CD.

I tried:
- no xorg.conf at all
- " Option "AutoAddDevices" "off" " in my xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
	Option "RandRRotation"  "on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2384 768
	EndSubSection
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"      
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option    	"Button2"    "3"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"    
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "ServerLayout"
#	Option "AutoAddDevices" "off"
        Identifier      "Default Layout"
	Screen      	"Screen0"
    	InputDevice    "Keyboard0" "CoreKeyboard"
    	InputDevice    "Mouse0" "CorePointer"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection
```

If you need more information, plese let me know 
and if you got some ideas, please let me know too

---


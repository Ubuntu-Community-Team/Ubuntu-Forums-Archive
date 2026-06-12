---
title: "Two finger scrolling"
date: 2011-07-15
forum: Hardware
---

### Post by simiasota on 2011-07-15
> **fi2 said:**
> ASUS K53SV
Ubuntu 11.04

nvidia GT540M - proprietary Nvidia driver does not work. Unity however starts and runs smoothly. 
Found the explanation [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=nvidia+optimus"). 

Compiz effects start with the care that is to be taken with 11.04.

New info: after recent update two finger scroll works.

New info: HDMI output: after recent automatic update HDMI works perfectly.

Standby mode is lazy to resume (about 1 minute).
So far I couldn't find any stable fix.

Overall performance is impressive, after several updates Ubuntu 11.04 seems to stabilize.
Hello, I have the same laptop but I can't get the two finger scroll work...

my synaptics-related packages are:
gpointing-device-settings ver. 1.5.1-4
gsynaptics 1.5.1-4
xserver-xorg-input-synaptics 1.3.99+git20110116.0e27ce3a-0ubuntu12.1

and the xorg.conf section for touchpad:

Section "InputDevice"
	Identifier	"Synaptics"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection


thank you in advance
francesco

---

### Post by foutes on 2011-07-15
> **simiasota said:**
> Hello, I have the same laptop but I can't get the two finger scroll work...

my synaptics-related packages are:
gpointing-device-settings ver. 1.5.1-4
gsynaptics 1.5.1-4
xserver-xorg-input-synaptics 1.3.99+git20110116.0e27ce3a-0ubuntu12.1

and the xorg.conf section for touchpad:

Section "InputDevice"
    Identifier    "Synaptics"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
    Option        "SHMConfig"        "on"
EndSection


thank you in advance
francesco
[CENTER][[IMG]http://edigitales.org/wp-content/uploads/2011/07/script-2-scroll.jpg[/IMG]]("http://edigitales.org/wp-content/uploads/2011/07/script-2-scroll.jpg")[/CENTER]

---


---
title: "Touchpad Settings - ??? KDE and Gnome"
date: 2009-11-24
forum: Hardware
---

### Post by Sugz on 2009-11-24
Okay, so 
Ive installed Ubuntu 9.10 (Fresh) and then added KDE later on.
However, I am unable to identify where both distros get their touchpad settings from.

As in Ubuntu, I get a different behaviour than in KDE. 

under both, typing the command, 

synclient -l

returns a different set of settings. 

if I type synclient -h

it returns 
"Cannot access shared memory area. SHMConfig disabled?"

even though it is ....

Also, I have created an Xorg.conf file with some settings and configurations *Below* and both seem to be ignoring those settings. 

secondly in KDE, I cannot seem to be able to drag and drop using the touchpad taps??

I ask this because in KDE, the touchpad is not as responsive as It is in Gnome, in Gnome, the touchpad is perfect, and I want to mirror this in KDE.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"	"on"
	Option		"HorizScrollDelta"	"350"
	Option		"VertEdgeScroll"	"350"
	Option		"VertTwoFingerScroll"	"1"
	Option		"HorizTwoFingerScroll"	"1"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"Tapbutton2"	"3"
	Option		"Tapbutton3"	"2"
	Option		"FingerLow"	"10"
	Option		"FingerHigh"	"30"
	Option		"MaxTapTime"	"180"
	Option		"VertScrollDelta"	"20"
	Option		"HorizScrollDelta"	"50"
	Option		"CircularScrolling"	"off"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"0"
	Option		"PalmDetect" 		"1"
	Option		"JumpyCursorThreshold"	"5"
	Option 		"FastTaps"		"1"
	Option		"FingerPress"		"200"
EndSection

Section "Module"
	Load "synaptics"
EndSection
```

Thank you for your help

---

### Post by rabidityfactor on 2009-11-24
try gsynaptics..
sudo apt-get install gsynaptics

it'l be installed in System->Prefrences->Touchpad

I do not know about KDE.

---

### Post by Sugz on 2009-11-24
I have gsynaptics already, and that does not affect the global touchpad settings, KDE just seems to completely ignore the synaptics settings that Gnome uses

---

### Post by marcopl on 2009-11-24
> **Sugz said:**
> I have gsynaptics already, and that does not affect the global touchpad settings, KDE just seems to completely ignore the synaptics settings that Gnome uses


pal...at least u got yr touchpad working.... i cant even get mine working....

[http://ubuntuforums.org/showthread.php?t=1333048](http://ubuntuforums.org/showthread.php?t=1333048)

---

### Post by Sugz on 2009-11-25
erm, i appreciate the feedback, but i wish you wouldn't hijack my thread fella.
this has had me well and truely stumped, I have even tried enabling SHMconfig using the new method specified as 9.10 apparently does not use gconf.config any more.

---

### Post by Sugz on 2009-11-26
This is a problem, which makes KDE very frustrating to use, any help at all is appreciated..

---


---
title: "Configure macbook: synaptics and pommed still don't work properly"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by ildella on 2007-02-06
After reading a lot of guide, particulary the "officiasl" ones on help.ubuntu.com and on debian wiki, I solved a lot of configuration problem with my macbook (core 2 duo) with a feisty up to date installed with a daily around 20th of january. 
Right now what is not working at all is synaptics toucpad driver which does not seems to be loaded. Either, if I do: 

cat /proc/bus/input/device

as said here: [http://tuxmobil.org/touchpad_driver.html](http://tuxmobil.org/touchpad_driver.html)
I can't see anything about synaptics. I have added configurations in xorg.conf ([http://www.popies.net/atp/](http://www.popies.net/atp/)) but no change. gsynaptics still said that SHMConfig is disabled and also syndaemon tells that it is not enabled. 
As a note, in xorg.conf I mount synaptics it in "/dev/psaux" cause "/dev/input/mice" is used by a usb logitech mouse that is configured in this way:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

this is what I find after installation, no manual change on this. The only change was to remove every InputDevice that used wacom driver from the ServerLayout and add the Synaptics Touchpad. 
BTW, touchpad works but I cannot use advanced configuration that synaptics driver allows to do, in particular the ability to "sleep while typing" is missing and this is very annoying. 


At last, the pommed matter. Pommed installed good and make the backlight keys work properly. I want to make Fn behavior change to get standard function behavior for first, but changing values in /etc/pommed.conf doesn't change anything. 

That's all, every other things works well in feisty, I am going to write a little up to date guide: on the net I only find guide that talk about edgy configuration with sometimes feisty updates. I just need to fix this two problems before :)

Thanks.

---

### Post by pouns on 2007-02-09
Hi,
i'm under edgy with 2.6.20. I have this in xorg.conf and touchpad works :
Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "SendCoreEvents"        "true"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "auto-dev"
 Option          "LeftEdge"      "100"
Option          "RightEdge"     "1120"
Option          "TopEdge"       "50"
Option          "BottomEdge"    "310"
Option          "FingerLow"     "25"
Option          "FingerHigh"    "30"
Option          "MaxTapMove"    "220"
Option          "TapButton1"    "1"
Option          "TapButton2"    "3"
Option          "TapButton3"    "2"
Option          "SHMConfig"     "on"
Option          "MinSpeed"      "0.79"
Option          "MaxSpeed"      "0.88"
Option          "AccelFactor"   "0.0015"
Option          "SHMConfig"     "true"
EndSection

you have to change the Identifier in your Section "ServerLayout". 
The module appletouch have to be load. Add it in /etc/modules if is not.
By

---

### Post by martinbures on 2007-04-26
So what does one add to the /etc/modules, and how does one do it?  I tried doing what was on the debian macbook wiki to load the module but it seems like the modules are different in Ubuntu from Debian. 

Thanks for your help.
martin.

---


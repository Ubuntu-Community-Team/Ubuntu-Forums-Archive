---
title: "&quot;Cleanest&quot; way to disable touchpad input?"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by Gaesadair on 2007-06-13
Hi,

I'm on an Asus s5000, and use my laptop only with a mouse plugged in. The touchpad on the PC is way too sensitive, and sometimes not sensitive enough - sometimes ahwne I'm typing and not even near the touchpad it will suddenly register a tap as if I clicked it. Now, I would like to disable it.

There is a Fn-button combination to disable the mousepad, however this does not work under Linux. I've verified that it works under Windows, so it is most likely solved in software drivers, not in hardware. Hence the Fn-button combination is useless for disabling the touchpad.

I've found the following block in my xorg.conf file:
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

Should I comment out the whole block? Change "SendCoreEvents" to "false"? What's the cleanest way to disable the touchpad without touching other parts of the system? Is the synaptics driver used for anything else?

Thanks in advance for any help.

---

### Post by tgoose on 2007-06-13
I think commenting out the whole block is the best idea.

Oddly, the Synaptics driver works fine for my laptop, which I'd have thought is the same chipset. But if you don't want to use it at all, commenting it all out should work fine.

---

### Post by Gaesadair on 2007-06-13
Thanks for your help.

It might not be the driver that's the problem - it might be the touchpad itself. It's placed on a place on the laptop that gets pretty hot, and the laptop has been running for quite some time.

---

### Post by shae on 2007-06-13
personally I think you should try installing gsynaptic through synaptic and changing the entery in xorg.conf to 
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"	"on"
EndSection
```

Then you can adjust and turn off your touch pad through a gui in System>Pref>Touchpad

---

### Post by neptho on 2007-06-14
> **shae said:**
> personally I think you should try installing gsynaptic through synaptic and changing the entery in xorg.conf to 
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"	"on"
EndSection
```

Then you can adjust and turn off your touch pad through a gui in System>Pref>Touchpad

This, and running 'syndaemon -d' (Add an entry into System->Preferences->Sessions) will allow you to disable the trackpad when typing, and when using an external mouse.

---

### Post by PietreWitobi on 2007-06-14
While you, as I see now, can solve it in software - I would just unscrew the casing to your laptop and disconnect it in the hardware.

That's what I did.

---

### Post by kerry_s on 2007-06-14
Just add this line to turn the tap to 0> Option "MaxTapTime"	"0"
that will disable tapping and you can still use the touchpad for moving around and scrolling, if you want to. Other wise just use this line->


Option "TouchpadOff"	"1"


TouchpadOff (Integer) 
Switch off the touchpad. Valid values are:
0 	Touchpad is enabled 
1 	Touchpad is switched off 
2 	Only tapping and scrolling is switched off

---


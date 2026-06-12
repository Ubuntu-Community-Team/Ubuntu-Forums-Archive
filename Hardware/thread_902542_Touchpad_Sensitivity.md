---
title: "Touchpad Sensitivity"
date: 2008-08-27
forum: Hardware
---

### Post by Keymaster on 2008-08-27
How can I make the touchpad sensitivity higher in Ubuntu 8.04 on a Dell Latitude D630?  Thanks.

---

### Post by mocoloco on 2008-08-28
If you haven't already, install gsynaptics, which requires you to set a line in your xorg.conf file for "SHMConfig".  Follow the [guide on Synaptics Touchpad]("https://help.ubuntu.com/community/SynapticsTouchpad"), which includes a bunch more info.

On my Dell Inspiron 1420 the gui tool barely changes sensitivity, and I had to set additional minspeed, and maxspeed stuff in xorg.  Here's what my section for the touchpad looks like.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"50"
#	Option 		"HorizScrollDelta" 	"0"
	Option		"MinSpeed" 	"0.7"
	Option		"MaxSpeed" 	"0.7"
#	Option		"AccelFactor"	"0.0010"
	Option		"SHMConfig"	"true"
EndSection
```

Not sure what the two commented lines were ever for.  If you use any of those you might have to play with the values to get them to your liking, and you'll have to restart X11 each time.

---

### Post by Keymaster on 2008-08-28
Thanks.  I'll look into that.
I know
```
Option 		"HorizScrollDelta" 	"0"
```
If you uncommented it, you wouldn't be able to use your touchpad's outer edge to scroll horizontal scrollbars anymore.  I hate that feature, so I have horizontal, and vertical scrolling turned off.  I also have "MaxTapTime" set to "0", because I hate tap to click.  My palm tends to hit the touchpad when I type.Here is my current touchpad configuration:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"MaxTapTime"		"0"
	Option		"VertScrollDelta"	"0"
```

---

### Post by mocoloco on 2008-08-28
I hate tapping too, I've been able to turn it off in the GUI, oddly enough it has to be off under both mouse and touchpad settings.  Glad I didn't have to turn it off in X because my wife likes it on for her user.
Guess that explains why I commented the scrolling line, since I like that feature turned on. Just noticed the syndaemon in that guide, I should try that since I sometimes accidentally bump scrolling while typing.

---

### Post by Keymaster on 2008-08-28
Well thanks for the advice before about what to do with the toucpad sensitivity.  I'll attempt it once I get home.

---


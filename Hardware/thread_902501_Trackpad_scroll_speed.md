---
title: "Trackpad scroll speed"
date: 2008-08-27
forum: Hardware
---

### Post by tct70 on 2008-08-27
Hi,

I'm new here and would like first of all to say that I think Ubuntu is fantastic!

I have an HP Compaq nx6130 Notebook PC which runs Ubuntu 8.04 like a dream.  I do however have one small issue.  I have a scroll section on my touchpad which scrolls 10 times faster than it does under windows.  It will scroll from the top of a document or web page straight to the bottom with only the slightest touch.  I've looked in the settings area for the touchpad but it does not have anything to adjust the speed.

I have looked at length on these forums for an answer, but have had no luck (probably missed it though).

It really is extremely annoying!

Any help would be very much appreciated.

Thanks

---

### Post by mocoloco on 2008-08-28
If you haven't already, install gsynaptics, which requires you to set a line in your xorg.conf file for "SHMConfig".  Follow the [guide on Synaptics Touchpad]("https://help.ubuntu.com/community/SynapticsTouchpad"), which includes a bunch more info.  Hopefully that's all you'll need to change.

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


---
title: "More Touchpad Problems"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by Tonren on 2006-06-15
Hi all.  I'm on an HP Compaq Presario v2565us.  I've sifted through every single touchpad thread on the forums, and I STILL can't completely disable Tap To Click.  Right now I've gotten to the point where a single tap won't click, but a DOUBLE tap will click, and that completely screws everything up until I click with the "actual" mouse button.

Here's the entry from my xorg.conf:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"	# added by Max
	Option		"SHMConfig"		"on"	# added by Max
EndSection

I tried fixing this with qsynaptics, but it didn't work.  Changes I make in qsynaptics don't seem to have any effect at all.  Correct me if I'm wrong, but hitting Ctrl + Alt + Backspace to reset Xorg should be enough to make changes completely propogate, right?  I tried resetting completely and it didn't work either, but I figured I ought to ask.

How do I know if I have a 'true synaptics' or 'alps' touchpad?

Thanks all!

---

### Post by jtbl on 2006-06-15
I have the same problem with my Presario R3000z laptop running the AMD64 version of Dapper, however I don't have this problem on the i386 version.  The way I fixed it was to download and install the newer synaptics drivers from the debian repos.

---

### Post by blackpaw on 2006-06-19
hello!

[QUOTE=Tonren]How do I know if I have a 'true synaptics' or 'alps' touchpad?
[/QUOTE]

on a console enter
```
 cat /proc/bus/input/devices
```

mine reads:
> [...]
I: Bus=0011 Vendor=0002 Product=0008 Version=5322
**N: Name="AlpsPS/2 ALPS GlidePoint"**
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1
[...]
 

I think I have an AlpsPS/2 ALPS GlidePoint Touchpad, then :P

using qsynaptics worked like a charm. circular scrolling is awesome :cool: 


andreas

---

### Post by Tonren on 2006-06-19
Looks like mine's a true Synaptics... knowing that I think I'll look back through the other threads and try again.  So far it still freaks out occasionally.

---

### Post by Tonren on 2006-06-21
Hey guys... still no luck.  I definitely have a Synaptics touchpad (not Alps), but qsynaptics doesn't change a thing, and my xorg.conf won't shut off tapping.  Any other suggestions...?

---

### Post by vincebs on 2006-06-23
How about MaxDoubleTapTime=0?

---


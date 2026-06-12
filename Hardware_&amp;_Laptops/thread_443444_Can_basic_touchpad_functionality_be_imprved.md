---
title: "Can basic touchpad functionality be imprved?"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Jason Pettitt on 2007-05-14
Hi,
Finally got a laptop (Toshiba Satellite A-100). Ubuntu has gone on very smoothly, after discovering that the Toshiba Recovery CD obliterates everything on the hard drive so Vista has to be installed, de-fragged and then resized *before* Ubuntu. A curse of hairy spiders on you Toshiba!

Anyhow, it's all good except the touch pad which is so so. It works fine, but only has very basic functionality, I'm wondering if there is a Gnome friendly app that can be recommended for configuring the touchpad or set up shortcuts/gestures for scrolling and the like. I've found reference to **gsynaptic** searching the forums, but my touch pad is only identified as a bog standard mouse in /etc/xorg.conf

Thanks,
Jay.

---

### Post by chayzer on 2007-05-14
Just installed ubuntu on my toshiba a-105 last night.  Have pretty much the same functionality as i did in windows. Scrolling, max/min and stuff all seem to work fine. Checked my xorg.conf and found I have this in there:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Not sure if that's any help.

---

### Post by Jason Pettitt on 2007-05-14
Yes it did, thanks very much.

I also added an **InputDevice "Synaptic Touchpad"** line to the **"ServerLayout"** section and installed gsynaptics package, hray!!!

---


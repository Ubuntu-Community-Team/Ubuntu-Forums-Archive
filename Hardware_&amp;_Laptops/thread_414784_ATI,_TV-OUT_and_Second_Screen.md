---
title: "ATI, TV-OUT and Second Screen"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by iraiscoming223 on 2007-04-20
Hi there, I've been looking around for a similar post, but I didn't find it.
I'm running Ubuntu Edgy right now, and I'm not looking forward to upgrade, as long as I solve the small issue I have right now.

The problem is that I cannot switch from my laptop screen to tv-out or screen-port. The only way to make my external screen works is to connect it before booting the computer. And, sometimes, it's the only working screen (I mean, if I connect my screen the laptop one will not work anymore). And if it is, I can't still play videos on it, black screen. -.-

I guess it's X's problem (or, at least, ATI drivers' problem). I can't get rid of it. Does anyone have any suggestion? Thanks in advance! 

Here is the device section in xorg.conf, it may be useful:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X600 (RV380)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps" "1"
EndSection
```

---

### Post by iraiscoming223 on 2007-04-21
Sorry about this, but...  **UP** :lolflag:

---


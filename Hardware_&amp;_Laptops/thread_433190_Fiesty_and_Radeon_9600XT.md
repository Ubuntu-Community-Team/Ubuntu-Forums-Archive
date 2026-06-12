---
title: "Fiesty and Radeon 9600XT"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by tanis143 on 2007-05-04
Ok, so far I've learned a lot about linux (though I'm still struggling to learn the "basics", like making scripts, learning where everything is, etc) but I've not been able to figure out why I can not go higher than 1024x768 using the restricted ATI drivers. Here is what my xorg.conf looks like in ref to my vid card:

Section "Device"
	Identifier  "ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:2:0:0"
EndSection

The thing that gets me is that busid, should it not be AGP? This is an AGP card. Other than that, I've updated my vid driver and tried searching for this problem, but only ones I've found were for nvidia or intel/mac with ATI. Anyone know where to point me?

---


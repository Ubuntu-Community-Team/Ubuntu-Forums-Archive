---
title: "ATI 200m Kubuntu"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by reddingae on 2007-04-25
I followed this walkthrough

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Everything went through without a hitch, except for that the "fglrxinfo" brings up:

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

instead of the 

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6458 (8.36.5)

that is should bring up (yes, I realize that I do not have the same card as this guy)

but my xorg.conf file says

Section "Device"
	Identifier	"ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

just like it should.

Am I missing something?

I am relatively new to the whole linux thing. By that I mean when I was younger I got my hands on a Red Hat distro and played with it for a few days, had no idea what I was doing, and re-installed windows. And I have been playing with the various versions of Ubuntu for the last week.

---

### Post by stearic on 2007-04-25
I'm no expert here, i'm in the same boat. But i believe in your xorg.conf file where it says driver, instead of ati it should be reading fglrx. I'm not at my laptop atm so i can't be sure, but i believe thats what it should be reading. I'm still working on getting full exceleration myself.

---

### Post by reddingae on 2007-04-25
I am not entirely sure what I did, but I got a "black screen of death" re-installed, and followed a much shorter install howto, and it worked. So I am happy now. Thank you.

---

### Post by strabes on 2007-04-25
Method 1 is much easier than method 2 on that page. That's the method I have always used to install my terrible fglrx drivers.

---


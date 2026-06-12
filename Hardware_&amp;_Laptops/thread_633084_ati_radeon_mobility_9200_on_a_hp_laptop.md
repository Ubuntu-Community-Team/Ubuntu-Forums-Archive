---
title: "ati radeon mobility 9200 on a hp laptop"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by brunoscunha on 2007-12-06
I'm having problems with my ati radeon mobility 9200.
First I can't play enemy territory, the screen is always flickering and i can't enable the visual effects in normal. The msg I get is can't enable visual effects.
I have installed the xorg-driver-fglrx.
I've edited the xorg.conf and here is the result

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	**Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"**
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection

I guess maybe that's the problem. I thought I had a ati radeon mobility 9200, but in fact I have a firegl mobility.
Is there any way to correct this or at least have the graphics card to have a decent performance.
On fiesty it worked perfectely, but after upgrade and also on a clean gutsy install the problems continue
Specs
HP/Compaq nx 7010
ram: 512
hd: 60 GB
GC: radeon mobility 9200 (at least thats what it says in the sitcker)

I-m runing out of options on how to make it work properly, any thoughts?

Thanks

---

### Post by brunoscunha on 2007-12-07
*bump*

---


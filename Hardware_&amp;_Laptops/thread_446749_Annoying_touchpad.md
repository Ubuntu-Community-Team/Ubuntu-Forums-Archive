---
title: "Annoying touchpad"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by kennythegeek on 2007-05-17
Hi.
I just installed feisty fawn on my old HP Compaq nx7000 because there was gfx problems with dapper drake.
But now the scroll area of the touchpad is 1/3 of the touchpad, instead of 1/5 as it should be... any way to change that? its should be a synaptics ps/2 touchpad.

[System]
HP Compaq nx7000 (Agency Series PP2080)
Intel Pentium M Centrino 1,4 GHz
ATi Mobility Radeon 9200
40 GiB HDD

[Ubuntu Setup]
Ubuntu 7.04 Feisty Fawn
XFCE 4.0

---

### Post by zjameria on 2007-05-20
I have the same problem. Additionally, in my laptop's touchpad, there is a designated strip on right side for vertical scrolling. When I enable vertical scrolling from qsynaptic, the vertical strip and regular touchpad both have vertical scrolling enabled. So then, I'd have two vertical scrolling spaces. The vertical scrolling in the regular touchpad uses up almost 1/3 of the space. If I disable vertical scrolling, then both vertical scrollings are disabled. I hope this makes sense. A solution to this problem would be greatly appreciated.

---

### Post by teachop on 2007-05-20
You can reduce the size of the scroll area by edit of the xorg.conf file using "sudo gedit /etc/X11/xorg.conf".  I think you can mess up xorg.conf so x cannot start, use care.  Changes don't take effect until you restart x if I remember.

The parameter I used to fix this was "RightEdge".  You can read about it with "man synaptics".  This is what I ended up with, but I think it varies all over from model to model:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MinSpeed"	"0.18"
	Option		"MaxSpeed"	"0.36"
	Option		"RightEdge"	"5650"
EndSection

The other big thing I needed to change was the speed.  It was so s-l-o-w!

---


---
title: "Intel 950 on Dell e1505"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by xonecas on 2006-06-17
i'm stuck on 1024x768, and I should have 1280x800.
I browsed around all of the forum, can't find a way to get my resolution right.
Apt-get can't find the 915resolution (even if I enable the "Universe" on sources.list (/etc/apt)
I also tried to reconfigure x, didn't work either.
heres is the piece of xorg.conf that mathers:

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection


Can someone help me.

BTW i'm not very used to Linux, so be patient with me please.

---

### Post by jjcv on 2006-06-17
Check out this website.... same model different number.

[http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/](http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/)

---

### Post by voidPtr on 2006-06-17
Enable universe in /etc/apt/sources.list

apt-get update

apt-get install 915resolution

reboot

enjoy

---


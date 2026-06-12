---
title: "P4M890T-M2 &amp; Gutsy"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by penguinfan on 2007-10-21
Guys and Gals

Help me pls. I hav the following issue with this motherboard.

Specs:
[http://www.shopping.com/xPF-Elitegroup-MB-ECS-P4M890T-M2-V1-0B-P4M890](http://www.shopping.com/xPF-Elitegroup-MB-ECS-P4M890T-M2-V1-0B-P4M890)
ECS motherboard, 3GHz Intel P4 3GHz (800 FSB) CPU, 1 x 512mb DDR-400 Ram, 1x PCI Express x16 slot with with Nvidia GIGA-BYTE GV-N7200 Graphics card, VIA Rhine Family Fast Ethernet Adapter, etc

My xorg.conf
Section "Device"
	Identifier	"nVidia Corporation G72 [GeForce 7300 SE]"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72 [GeForce 7300 SE]"
	Monitor		"DELL P790"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

I have custom visual effects enabled and restricted drivers.

My issue is that my system freezes after a certain amount of time showing off my visual effects. This really hurts my reputation as a Show Off :). This only happens when the CPU is really working hard.
The mouse, sound and video freezes completely. Not even a Ctrl, Alt Backspace will help me. The only option is to restart the pc.

any help will b appreciated. Thanx

PS other then this; Gutsy Rocks.

---

### Post by penguinfan on 2007-10-21
Anyone???

---

### Post by penguinfan on 2007-10-23
It seems the latest Nvidia drivers (NVIDIA-Linux-x86-100.14.23-pkg1.run) from their website did the trick for me.
Now back to showing off :)

---


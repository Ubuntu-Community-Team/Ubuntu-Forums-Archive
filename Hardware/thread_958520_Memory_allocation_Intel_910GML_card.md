---
title: "Memory allocation Intel 910GML card"
date: 2008-10-25
forum: Hardware
---

### Post by Evgeny_N on 2008-10-25
Dear Sirs, do Ubuntu support dynamic video memory allocation? Video card supports allocation up to 128 Mb from system memory, but actually graphics are very slow that seems to be that video memory do not exceed 8Mb.
Please tell me how could I check video memory volume & how to make dynamic allocation possible.
Some info from [http://alcor.concordia.ca/manpages/sys4/intel.4.html:](http://alcor.concordia.ca/manpages/sys4/intel.4.html:)
"For the 830M and later, this is required in order for the driver to use more video ram than has been pre-allocated at boot time by the BIOS. This is usually achieved with an "agpgart" or "agp" kernel driver. Linux, FreeBSD, OpenBSD, NetBSD, and Solaris have such kernel drivers available" - Do Ubuntu got?
"By default, the i810 will use 8 megabytes of system memory for graphics. For the 830M and later, the driver will automatically size its memory allocation according to the features it will support. The VideoRam option, which in the past had been necessary to allow more than some small amount of memory to be allocated, is now ignored."

My xorg.conf (video&modules):
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	#VideoRam 	131072 #Parameter disabled by driver
EndSection

---


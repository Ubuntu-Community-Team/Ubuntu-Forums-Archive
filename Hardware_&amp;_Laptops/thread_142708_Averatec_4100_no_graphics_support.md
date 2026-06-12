---
title: "Averatec 4100 no graphics support?"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by Liquid1101 on 2006-03-11
when i run glxgears its so slow that it won't even report fps... any idea's on what may need to be done? I've read through looking for similar problems but havn't found any

---

### Post by Liquid1101 on 2006-03-11
Copy and paste from /etc/xorg.conf

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

------------------------------------------
Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) SiS Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1

---

### Post by patrickfromspain on 2006-03-11
From xorg.conf, you should copy the Section "Device", which refers to the grafic card.

Also... What's the output of glxinfo | grep "direct" ?

---

### Post by Liquid1101 on 2006-03-11
oops i did mean to copy that section, i'll get that posted up when i get home from work, sorry about that.

---

### Post by Liquid1101 on 2006-03-13
glxinfo output. Should the direct rendering be Yes?
> 
liquid@liquid:~$ glxinfo | grep "direct"
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


and the device section of my xorg.conf

> Section "Device"
        Identifier      "Silicon Integrated Systems (SiS) SiS Default Card"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection


---

### Post by Liquid1101 on 2006-03-25
still been searching online but to no help. anyone have any idea's?

---


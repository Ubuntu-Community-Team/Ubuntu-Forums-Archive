---
title: "[netbook] Improve Intel 945GSE graphics"
date: 2009-03-30
forum: Hardware
---

### Post by dfoxpro on 2009-03-30
Hello

this week i bough a 3e-pc-1k-ha
> 
Intel® Atom™ Processor N270 (512K Cache, 1.60 GHz, 533 MHz FSB)

Mobile Intel® 945GSE Express Chipset
82801GBM I/O Controller
82945GSE Graphics and Memory Controller

512gB ram
160gB hdd


and install ubuntu on this machine (because this have the w.ms oem installation ¬¬).

after installing all the "drivers" for 3epc i look for improve the graphic capability.


by default the std installation recognize the i945 series chip-set with 
(+/-) 2500 frames in 5.0 seconds = 500 FPS

then i put the typically mods of the xconf:

```

Section "Module"
	Load "dri"
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option "AperTexSize" "262144"
	Option "TripleBuffer" "true"
	Option "PageFlip" "true"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GME Express Integrated Graphics Controller"
EndSection

```

but after all,only gains a (+/-)125 fps ¬¬
(+/-) 3243 frames in 5.0 seconds = 648.571 FPS


Now i want to make this better. U know how?

Please help me(us).

PD:i want 2 play WoW in this netbook XD

---

### Post by bornagainpenguin on 2009-05-23
/BUMP for interest...

---

### Post by garethpn on 2010-11-23
> 512gB ram

Wow! Impressive! ;)

---


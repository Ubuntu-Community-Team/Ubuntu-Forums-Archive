---
title: "ATI RADEAN 7000... How to install it?"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by kwiki on 2007-04-12
I've been searching for a week looking for a how to setup this video card on my Ubuntu PC but have no luck finding one... anyone here know how to do it??

---

### Post by Ek0nomik on 2007-04-13
It's not an open source driver, but it may do the trick:  [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by eXisor on 2007-04-13
> **kwiki said:**
> I've been searching for a week looking for a how to setup this video card on my Ubuntu PC but have no luck finding one... anyone here know how to do it??

I have a Radeon 7000 VE 64mb agp 4x running in Edgy (Dapper would not do 3D), using the standard 'radeon' driver that comes with xorg. I use AIGLX for 3D and have Beryl running quite well (no water, but most everything else works).

Below is the device section of my /etc/X11/xorg.conf

```
Section "Device"
	Option		"AGPMode"		"4"
	Option		"AGPSize"		"128"
	Option		"GARTSize"		"64"
	Option 		"ColorTiling" 		"true"
	Option 		"EnablePageFlip"	"true"
	Option 		"AccelMethod" 		"XAA"
	Option 		"XAANoOffScreenPixmaps" "true"
	Option 		"AGPFastWrite" 		"true"
	Option 		"BackingStore" 		"true"
	Option 		"SubPixelOrder" 	"NONE"
	Option 		"DynamicClocks"		"true"
	Option		"RenderAccel"		"true"

	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
EndSection
```

I also included dbe (double-buffering) in the module section 

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```

and have a DRI section as well

```
Section "DRI"
	Mode	0666
EndSection
```


That's all it takes.

---

### Post by kwiki on 2007-04-15
thanks for the relies gentlemen i'll try what you've suggested and i will post the result later.. again thank you very much....

---


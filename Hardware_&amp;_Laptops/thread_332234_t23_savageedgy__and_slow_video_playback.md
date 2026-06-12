---
title: "t23 savage/edgy  and slow video playback"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by liamk on 2007-01-05
hi,

I have problem with slow  video playback. It looks a little like page tearing (no vsync on low monitor refresch rates) or no frame buffer.

I use:
ibm t23/SuperSavage IX/C
ubuntu 6.10
mplyer output Xv

I modified xorg.conf a little but it didn't help :/

```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"S3 Inc. SuperSavage IX/C SDR"
	Driver		"savage"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option		"BusType"		"AGP"
	Option		"DmaType"		"AGP"
	Option		"DmaMode"		"Vertex"
	Option		"AGPMode"		"2"
	Option		"AGPSize"		"16"
	Option		"SWCursor"		"true"

EndSection
```

any ideas ?

---


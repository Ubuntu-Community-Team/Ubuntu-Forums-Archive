---
title: "X3100 on a 64bit using 8.10"
date: 2009-02-12
forum: Hardware
---

### Post by dooco on 2009-02-12
i am having difficulty configuring my video.  it is an integrated card and i cant get a proper resolution  i am getting a max of 1024-768 which would be good on a smaller monitor but i got a 20"  can someone please help me configure this card my xorg.conf looks like
 
> Section "Device"
	Identifier	"Configured Video Device"
	Driver "intel"
	Option		"UseFBDev"		"true"
        Option "XaaNoPixmapCache"
 	Option "XAANoOffscreenPixmaps" "1"
 	Option "DRI" "true"
 	Option "AccelMethod" "XAA"
	VideoRam 440320
 	Option "XvMCSurfaces" "6"
 	Option "May_Need_ForceBIOS" "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"

---


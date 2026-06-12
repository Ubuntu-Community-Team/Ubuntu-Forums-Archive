---
title: "ATI Fusion HDMI Video not Working"
date: 2011-07-17
forum: Hardware
---

### Post by DdlyArcher on 2011-07-17
Hello,

I'm having a problem getting HDMI Video working so that I can connect my screen up a TV(Only One Display, Changed TV over to HDMI).  In Monitors and Catalyst it only allows for VGA output(Max 1360x768, Should be 1080P).

Ubuntu 11.04, 32 Bit
Latest ATI Drivers from ATI

Hardware
[ZOTAC FUSION350-A-E AMD E-350 APU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500068")


xrandr:
```
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 580mm x 320mm
   1360x768       60.0*+
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   1024x600       60.0  
   800x600        60.3  
   800x480        60.3  
   640x480        59.9  
```

Xorg.conf:
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:0:1:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I've googled for answers but all I come up with is people having probems with HDMI audio.
If you need any more information just ask.

Thank you for any help given,

---

### Post by bcl1713 on 2012-07-11
bump. same hardware.  I get the ubuntu splash screen but then the video goes away.  I have the catalyst drivers installed from the default repos and the program doesn't seem to see it.  hdmi video worked fine before i installed it but you can't use hdmi audio without it.. at a loss. :(

---


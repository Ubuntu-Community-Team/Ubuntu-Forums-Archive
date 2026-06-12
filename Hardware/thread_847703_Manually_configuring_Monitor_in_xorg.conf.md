---
title: "Manually configuring Monitor in xorg.conf"
date: 2008-07-02
forum: Hardware
---

### Post by Harry Muscle on 2008-07-02
I'm trying to manually tell x windows (or would it be gnome ...) which monitors are attached to my laptop since it doesn't detect them properly, however, I have a few questions.

First, how do I know what to use as the Identifier in the Monitor section of the xorg.conf file?  Is it just any name I choose?  Or does it have to be something specific?  If it's something specific where do I find this info?  If it's anything I choose, how do I tell it which monitor is which since I need to specify two monitors (internal display and external monitor)?

Thanks,
Harry

---

### Post by phidia on 2008-07-02
Information for manually configuring xorg in hardy is [here]("https://help.ubuntu.com/community/XORGHardy") but ATI cards are not mentioned at all and from your previous post I think that's what you have.
A more general guide which doesn't appear to handle you situation is [here]("https://help.ubuntu.com/community/Video").

---

### Post by Harry Muscle on 2008-07-02
Thanks but those links talk mostly about configuring the driver or device part of xorg.conf ... my concern I'm pretty sure is mainly the Monitor part.

Also another question I have is, how do I specify which resolutions the monitor can support.

Thanks,
Harry

---

### Post by phidia on 2008-07-02
There's a "monitor" section in xorg and the modelines list the rez & more. See mine below for example:

> Section "Monitor"
	Identifier	"Q9-2 Series"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0

---


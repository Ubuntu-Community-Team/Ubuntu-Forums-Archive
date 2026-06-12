---
title: "1680x1050 res *almost* working"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by JLAudioFan on 2007-04-27
Hello!

I've been banging my head against the wall trying to get this Sceptre NagaIII 20.1" Widescreen to work with my Toshiba m400 laptop.

I have been using the i810 drivers (although i have the intel 945 internal vid card) and tonight i found a post suggesting the regular "intel" drivers package.

Right now I can get the 2nd best resolution of 1280x720 to work just fine.

I've tried custom modelines, ran dpkg-reconfigure xserver-xorg more times than I can count.  Xserver tries to run 1680x1050 and almost does it right... but the picture is squished (empty bar on the left side of the monitor) and the refresh rate isn't right because there are pixels flickering on and off.

The sceptre monitor does 1680x1050 @ 60  but for the life of me, I can't get it to work!

Here's some info:

Sceptre monitor specs:
[http://www.sceptre.com/Products/LCD/Specifications/spec_x20g_NagaIII.htm]("http://www.sceptre.com/Products/LCD/Specifications/spec_x20g_NagaIII.htm")

xorg.conf:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	24-82
	VertRefresh	50-75
	DisplaySize 	433.44 270.90
	Modeline 	"1680x1050_60.00" 122.00 1680 1684 1700 1803 1050 1052 1064 1082 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```


I would really, really appreciate some help.  If there is anything else that I need to post please let me know.  

THANKS!!!

---

### Post by JLAudioFan on 2007-04-29
Noone has any ideas here?

---

### Post by roopesh on 2007-04-29
Unsure if it'll change anything, but I have "1680x1050_60" (notice no decimals) in my xorg.conf file.  Different monitor & card, but I had issues getting it all working, too.

---

### Post by JLAudioFan on 2007-04-30
I went through and took out the .00 in my xorg.conf, but it didn't change anything.  Would you mind posting part of your xorg.conf so I can take a look at it?

Thanks for your reply!

---

### Post by jamesford on 2007-04-30
i got mine working by deleting these lines
	HorizSync	24-82
	VertRefresh	50-75
	DisplaySize 	433.44 270.90

of course my lines had different values

---

### Post by JLAudioFan on 2007-04-30
Ok, I'll try that tonight when I get home.  Thanks.

---

### Post by JLAudioFan on 2007-05-02
Still no luck.  I'm really bummed out because i can tell it'll look wonderful when the 1680x1050 res works, because when i try to display it at that high of a resolution it is off center and flickery, but the resolution looks really good...

Anyone have other things I can try?

Here's some info from my /var/log/Xorg.0.log

```
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) intel(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) intel(0): Modeline "1280x1024"  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync
(II) intel(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) intel(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) intel(0): Modeline "1360x765"   84.50  1360 1432 1568 1776  765 768 773 795 -hsync +vsync
(II) intel(0): Modeline "1280x720"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
(II) intel(0): Modeline "1280x720"   95.75  1280 1360 1488 1696  720 723 728 755 -hsync +vsync
(II) intel(0): Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync
(II) intel(0): EDID vendor "SPT", prod id 8336
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
```

---

### Post by Riggs on 2007-05-07
> **jamesford said:**
> i got mine working by deleting these lines
	HorizSync	24-82
	VertRefresh	50-75
	DisplaySize 	433.44 270.90

of course my lines had different values

This did it for me too.  Working very nicely.  No need for modelines whatsoever.

---

### Post by zavizionov on 2007-10-11
I'm not sure, but maybe this help you
[http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html](http://zavizionov.blogspot.com/2007/09/howto-ubuntu-intel-945-widescreen.html)

---


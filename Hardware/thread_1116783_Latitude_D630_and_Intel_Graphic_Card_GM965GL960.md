---
title: "Latitude D630 and Intel Graphic Card GM965/GL960"
date: 2009-04-05
forum: Hardware
---

### Post by lorebett on 2009-04-05
Hi

I've been using Linux on this laptop for more than one year now, and with kubunut 7.10 I was using the intel driver in the xorg configuration file, for the graphic card:

[INDENT]Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/INDENT]

Now, I tried and install new versions: kubuntu 8.04 and jaunty 9.04 (beta) and noted that the xorg.conf file does not specify any graphic card:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Thus, I assume it's using the simple vesa driver?

Speciall 3d effects work, but they're slow...

should I manually put the intel driver specification in the xorg.conf file (by the way, I see no configuration dialog in gnome and kde menus for the graphic card configuration...).

any suggestion please?

---


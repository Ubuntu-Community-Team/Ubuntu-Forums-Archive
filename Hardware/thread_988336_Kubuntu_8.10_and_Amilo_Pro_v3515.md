---
title: "Kubuntu 8.10 and Amilo Pro v3515"
date: 2008-11-20
forum: Hardware
---

### Post by FredDie3785 on 2008-11-20
Hell-o every1!
I've just installed Kubuntu 8.10 on my Amilo Pro v3515. I used alternate CD, just in case. The installation went fine, but when it tries to boot KDE it hangs. The whole screen is messed up (attachment).

I know that running graphic mode on vn896 chipset is possible, because somehow I've managed to do it (I don't remember how). Now I'm totally confused what I should write in xorg.conf.
Maybe someone could help. 
Here's my xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"openchrome"
	Option		"XaaNoImageWriteRect"
	Option 		"HWCursor" "false"
	Option 		"SWCursor" "true"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual 1280 800
	EndSubSection
EndSection
```

---

### Post by rstoya05-lx on 2008-11-20
I remember reading somewhere that in 8.10 the dependence on xorg.conf is significantly reduced. Looking at my own system, I do have xorg.conf but most sections are commented out.

I do run kubuntu as well and have had so much trouble with stability (periodic freezes) that I've switched to GNOME. If you search my posts I've posted about it but have not been able to resolve.

Under GNOME my experience is better but I still see occasional freezes and so far nothing in the logs to explain it.

---


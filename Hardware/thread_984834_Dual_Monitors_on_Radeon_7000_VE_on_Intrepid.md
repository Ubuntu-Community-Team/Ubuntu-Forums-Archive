---
title: "Dual Monitors on Radeon 7000 VE on Intrepid"
date: 2008-11-17
forum: Hardware
---

### Post by JazerB on 2008-11-17
Hello,

I have been trying to get a dual-head Radeon 7000 VE to run dual monitors.  I have been through the forums to see if anyone has had the same problem and it seems that they have.  However, I haven't been able to get the solution to work for me.

The articles that I have come across suggest the generic open source drivers should work with this card and I believe they do.  I just think I'm missing something in my xorg.conf.

I think I just need another set of eyes on it because it's got this noob stumped.

```

Section "Device"
	Identifier	"Radeon 7000-0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
	#Option		"XAANoOffscreenPixmaps"
EndSection

Section "Device"
	Identifier	"Radeon 7000-1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
	#Option		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"HP2105"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"SM205"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Left Screen"
	Monitor		"HP2105"
	Device		"Radeon 7000-0"
	DefaultDepth	24
	#SubSection "Display"
	#	Depth		24
	#	Modes		"1680x1050" "1440x900" "1024x768"
	#EndSubSection
EndSection

Section "Screen"
	Identifier	"Right Screen"
	Monitor		"SM205"
	Device		"Radeon 7000-1"
	DefaultDepth	24
	#SubSection "Display"
	#	Depth		24
	#	Modes		"1680x1050" "1440x900" "1024x768"
	#EndSubSection
EndSection

Section "Extensions"
	Option	"Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Left Screen" 0 0
	Screen		1 "Right Screen" RightOf "Left Screen"
	Option		"Xinerama" "true"
EndSection

```

I can post my logs as well if needed.  I just didn't want to use the space if this is just something that I am overlooking.

Thanks!
-b

---

### Post by JazerB on 2008-11-17
Obviously I'm not a big early adopter but I'm thinking about buying a Radeon 9800 Pro from a friend.  Would that be easier to configure?

Btw...bump:-P

---

### Post by Peter Brown on 2008-11-20
Here is an xorg.conf that works for me.

Section "Device"
        Identifier      "Radeon 7500"
        Driver          "radeon"
        Option          "Monitor-VGA-0" "Monitor A"
        Option          "Monitor-DVI-0" "Monitor B"
EndSection

Section "Monitor"
        Identifier      "Monitor A"
EndSection

Section "Monitor"
        Identifier      "Monitor B"
        Option          "LeftOf" "VGA-0"
EndSection

Section "Screen"
        Identifier      "Dual Screen"
        Monitor         "Monitor A"
        Device          "Radeon 7500"
        Subsection      "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

I'm using the radeon driver which supports randr. Info on randr at [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by JazerB on 2008-11-22
Thanks my friend.  I didn't have much luck with the 7000 but being the cheap ******* I am, I scored a Radeon 9800 from a buddy from work.  Seems to work well but, again being the linux noob, I have been having problems getting the desktop to extend to my second monitor.

In the interest of being all "anti establishment" I will trudge forward.

I really am digging Ubuntu so far; however, the dual monitor thing is trying my conviction.

Cheers! (tipping my delightful single barrel 10 year bourbon in your general direction)

---

### Post by GnuSense on 2009-03-12
Thanks, Peter Brown, that helped me a bunch.

> **Peter Brown said:**
> Here is an xorg.conf that works for me.

Section "Device"
        Identifier      "Radeon 7500"
        Driver          "radeon"
        Option          "Monitor-VGA-0" "Monitor A"
        Option          "Monitor-DVI-0" "Monitor B"
EndSection

Section "Monitor"
        Identifier      "Monitor A"
EndSection

Section "Monitor"
        Identifier      "Monitor B"
        Option          "LeftOf" "VGA-0"
EndSection

Section "Screen"
        Identifier      "Dual Screen"
        Monitor         "Monitor A"
        Device          "Radeon 7500"
        Subsection      "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

I'm using the radeon driver which supports randr. Info on randr at [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---


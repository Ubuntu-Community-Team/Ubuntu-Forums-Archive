---
title: "Xorg.conf Issues"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by ericinwisconsin on 2009-04-28
9.04 didn't detect either my video card or my monitor. The best I can get is 800x600. Here's my Xorg.conf file:

```

Section "Device"
        Identifier          "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

I have a Voodoo 5 5500 video card and a Sony SDM-HS93 monitor. If anyone can point me in the right direction, I'd appreciate it.

Eric

---

### Post by ericinwisconsin on 2009-04-28
Ok, I managed to get myself going in the right direction, BUT...

When I move a window, or use the mouse scroll wheel, the xserver reboots and I'm back to the KDM login. Here's my xorg.conf:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	VendorName	"Sony"
	ModelName	"Sony SDM-HS93"
	HorizSync	28-65
	VertRefresh	48-65

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"monitor1"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"True"
EndSection

```

If anyone can give me some pointers, I'd appreciate it.

Eric

---

### Post by ericinwisconsin on 2009-04-30
It appears that the problem is with my Voodoo 5 5500 card. Once I replaced it, everything started working properly. A little research revealed that there's a bug in the tdfx driver, which is used by this card. Since I don't want to use the poor-quality "vesda" driver, I decided to use another card.

---


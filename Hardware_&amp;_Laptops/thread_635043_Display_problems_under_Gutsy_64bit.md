---
title: "Display problems under Gutsy 64bit"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by CK1 on 2007-12-08
I have a fresh install of Ubuntu Gutsy 64bit and have 2 display problems. The first is that sometimes the screen does not refresh properly when changing between applications or the menus do not show unless you move the cursor over where the list should be. There is no consistent patten to when this happens, it can be just after login or at any other time. The only way around this is to re-boot. See snapshot.png file attached.

The second problem mainly happens using open office.  Lines are drawn all over the screen but after this they will also appear in a terminal session, see attachment snapshot-2.png.

I have a Foxconn motherboard with an on board graphics card. Output from lspci:-
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


This is an extract from my xorg,conf file :-

[PHP]Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	16
EndSection[/PHP]

I have tried changing xorg.conf to use the vesa driver but this made no difference.  I have changed the "Default depth" from 24 to 16 but again this has not cured the problems. I do not have    any desktop effects enabled.

Any help to resolve these issues will be much appreciated.

---


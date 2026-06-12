---
title: "Problem starting Xwindows"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by kapunga on 2006-04-24
I just got a Dell Inspiron E1505.  Xwindows doesn't seem to want to work regardless of how I reconfigure xserver-xorg.  It never even boots.  I've installed Breezy Badger.  My laptop's graphics controller chipset is Intel 945GM.

Here is the output to lspci:

> 
0000:00:00.0 Host bridge: Intel Corp.: Unknown device 27a0 (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp.: Unknown device 27a2 (rev 03)
0000:00:02.1 Display controller: Intel Corp.: Unknown device 27a6 (rev 03)0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corp.: Unknown device 27d6 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b9 (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c4 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd: Unknown device 0822 (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd: Unknown device 0592 (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd: Unknown device 0852 (rev 05)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)


Here is the end of my Xorg.0.log
> 
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


Here is what I believe to be the relevant part of my xorg.conf
> 
Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection



Any help would be much appreciated!
-Thor

---

### Post by dermotti on 2006-04-24
You try **vesa** as your driver?

---

### Post by kapunga on 2006-04-24
Tried vesa, no real difference.

---

### Post by tigrux on 2006-04-25
I have an e1505 too.

It does not work in Breezy.
You must upgrade to Dapper Beta.

This laptop works impresively well. :)

---


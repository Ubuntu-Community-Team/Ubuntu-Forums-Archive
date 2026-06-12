---
title: "Change Primary Monitor"
date: 2008-12-17
forum: Hardware
---

### Post by terribletrouble on 2008-12-17
Ubuntu Intrepid:

Laptop 1:
Laptop display: LVDS
External Samsung: VGA
All menus are always on the VGA, and not on the LVDS. If I choose mirror, then the VGA screen is not filled, LVDS = 1400x1050 and VGA=1680x1050.

Laptop 2: [Switching via KVM]
Laptop display: LVDS
External Samsung: VGA
All menus are always on the LVDS, and not on the VGA. If I choose mirror, then the VGA screen is not filled, LVDS = 1400x1050 and VGA=1680x1050.

How can I determine which monitor is primary? I want to change it....
My xorg.conf is blank!

---

### Post by terribletrouble on 2008-12-19
Bump!

---

### Post by JayCarman on 2008-12-19
If you are using an NVIDIA graphics card you can use a GUI program to edit your configuration. You can install from the Canonical-supported Open Source software (main) repository:

```
sudo apt-get install nvidia-settings
```

This will allow you to specify which monitor is the primary monitor.

Hope this helps!

---

### Post by terribletrouble on 2008-12-19
Sadly, not, it is an Intel based Chipset!

```

Slot:	00:00.0
Class:	Host bridge
Vendor:	Intel Corporation
Device:	Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
SVendor:	Hewlett-Packard Company
SDevice:	Device 30aa
Rev:	03

Slot:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 30aa
Rev:	03

Slot:	00:02.1
Class:	Display controller
Vendor:	Intel Corporation
Device:	Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 30aa
Rev:	03


```

If it was nvidia, it would be easy, this is hard.

What baffles me, how did it choose which one to make primary?

---

### Post by campbuds on 2009-01-24
Solution? I would like to change my primary monitor also

---


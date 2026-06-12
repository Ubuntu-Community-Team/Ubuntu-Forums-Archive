---
title: "how to enable ASUS Xonar DG?"
date: 2012-01-31
forum: Hardware
---

### Post by nazaroo2 on 2012-01-31
Does anyone here in hardware know how to get this card (Xonar DG) working?
I have a Dell Optiplex 330 (dualcore) w 4gig ram.
I disabled the onboard soundcard in BIOS. 


The Xonar card shows up with** lspci** in a terminal:

```
**[COLOR=Blue]# lspci[/COLOR]**
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 0a)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 0a)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)
[B][COLOR=Blue]03:02.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
# [/COLOR][/B]

```

---

### Post by nazaroo2 on 2012-02-01
*bump*

Nobody has a working Xonar card?

Somebody told me I need to install an older version of alsadriver. 
Does anyone know how to do that?

---

### Post by MoreOrLess on 2012-02-01
No, you need a newer version of alsa driver (1.0.24 or 1.0.25).

---


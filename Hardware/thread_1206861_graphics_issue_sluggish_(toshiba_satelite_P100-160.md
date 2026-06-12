---
title: "graphics issue? sluggish (toshiba satelite P100-160)"
date: 2009-07-07
forum: Hardware
---

### Post by iJammy on 2009-07-07
i've installed ubuntu, i've tried to run media center's such at boxee and moovida and they are pretty much unusable the graphics are so sluggish.

LSPCI 
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```some help or ideas on how to improve this?

---

### Post by shatterblast on 2009-07-07
You probably want the following from Synaptic:

X.Org X server -- Intel i8xx, i9xx display driver

Items designed for high-end graphics require hardware drivers.  I assume this as the issue since it seems your Ubuntu installation as a bit fresh.

Under the standard Gnome version of Ubuntu, Synaptic is under:

System -> Administration -> Synaptic

---

### Post by iJammy on 2009-07-07
ubuntu says this is already installed?

this laptop may only have an intel mobile chip, but before i put ubuntu on i could run autocad lt 2009 with out so much of a blink.

dont get me wrong, i'd rather ubuntu over microshiz anyday...

perhaps there is some setting on the driver i need to disable?

---

### Post by shatterblast on 2009-07-07
> **iJammy said:**
> ubuntu says this is already installed?

this laptop may only have an intel mobile chip, but before i put ubuntu on i could run autocad lt 2009 with out so much of a blink.


On both Windows and Linux, the Intel video driver uses part of your computer's RAM to simulate a video card's memory.  Since Linux comes across as more resource efficient, it relies more on the video driver for high-end graphics.  I would vote for AutoCAD as high-end.  The next step is using the updated Intel driver from the Karmic test version:

[http://packages.ubuntu.com/karmic/xserver-xorg-video-intel](http://packages.ubuntu.com/karmic/xserver-xorg-video-intel)

> **iJammy said:**
> 
perhaps there is some setting on the driver i need to disable?

Setting the extra Visual Effects to minimal would help, which exists in the Appearance window.  To reach it, go to:

System -> Preferences -> Appearance -> the Visual Effects tab at the top -> set to None.

---


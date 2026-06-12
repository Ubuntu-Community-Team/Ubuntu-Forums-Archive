---
title: "New install of ubuntu netbook on MSI Wind 420 US"
date: 2009-05-02
forum: Hardware
---

### Post by robfindlay on 2009-05-02
Everything works out of the box....except....my screen res is locked into 800x600 on my 19 inch LCD for dual boot....can someone remind me of the file you have to edit to fix that?

Also is there anyway to get just a NORMAL looking desktop?

TIA....

---

### Post by }SoC{phenix on 2009-05-02
What kind of graphics card does you computer have?  The drivers that Ubuntu uses could affect that.  I've noticed that when using the vesa drivers I haven't been able to get above 800x600.  The kind of graphics card your using could affect the drivers that Ubuntu uses.

As far as the second question goes, what do you mean when you ask if there is a normal desktop?  If you just don't like the taskbar's positioning that's a fairly easy issue to fix.

---

### Post by robfindlay on 2009-05-02
> **}SoC{phenix said:**
> What kind of graphics card does you computer have?  The drivers that Ubuntu uses could affect that.  I've noticed that when using the vesa drivers I haven't been able to get above 800x600.  The kind of graphics card your using could affect the drivers that Ubuntu uses.

As far as the second question goes, what do you mean when you ask if there is a normal desktop?  If you just don't like the taskbar's positioning that's a fairly easy issue to fix.


my LSPCI: 

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

Not sure where to find the driver info

---


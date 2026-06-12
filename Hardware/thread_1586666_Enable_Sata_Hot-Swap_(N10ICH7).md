---
title: "Enable Sata Hot-Swap (N10/ICH7)"
date: 2010-10-02
forum: Hardware
---

### Post by poscaman on 2010-10-02
Hello everyone

My desktop has [this]("http://www.asus.com/product.aspx?P_ID=X70d3NCzH2DE9vWH") motherboard and lspci shows these:
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet Adapter (rev b0)
04:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

```

So, it seems that sata controller is N10/ICH7. Is there a possibility to enable hot-swap with this controller, under Ubuntu 10.04?

Thanks a lot

---

### Post by Ed_Ziffel on 2010-10-02
That 945 chip set is at least 6 years old.  Never heard of anyone doing a hot swap with it period much less with Ubuntu.  No point in doing a hot swap with out a raid 0 config, and then only in a high volume production situation.  Easy button: just turn it off.

---


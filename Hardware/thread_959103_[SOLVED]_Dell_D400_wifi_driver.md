---
title: "[SOLVED] Dell D400 wifi driver"
date: 2008-10-26
forum: Hardware
---

### Post by Newy11 on 2008-10-26
Gday all, if this has been covered before i cant seem to find any helpful info anywhere.

I have a Dell Latitude D400 and im trying to get the wifi to work on it. when running the lspci this is the output:

```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
01:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
01:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
01:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

so as you can see it has the Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter and i have looked for ages trying to find the right way to get this to work. I am very limited with my linux skills. If anyone could shed some light on this that would be much appreciated :)

---

### Post by Newy11 on 2008-10-26
bump

---

### Post by Newy11 on 2008-10-26
solved, installed 8.10 and all worked straight away. thanks to all those helpful posts there ;)

---


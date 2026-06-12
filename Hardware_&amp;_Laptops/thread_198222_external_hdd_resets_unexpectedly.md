---
title: "external hdd resets unexpectedly"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by Aurelias on 2006-06-16
Hey all, I have two external USB 2 hard drives that both experience strange behavior under Dapper.  When plugged in, hotplug recognizes them fine and the appropriate icons show up on the desktop, but after opening and using them for a while, they seem to "reset".  That is, they unmount themselves and appear as though they were just plugged in again.  When I disable the ehci drivers and force USB 1.1 to be used, this does not happen, though I'd far prefer to use USB 2 for the speed boost.  Also, the time from mounting either drive to it resetting is seemingly random and unrelated to disk access, heat, etc.  Does anyone know if the ehci drivers in Ubuntu 2.6.15 kernels are buggy, or is it some quirk of my USB controller?
Thanks,
Aurelias

Here's my basic lspci output, in case it helps:
```
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0000:06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)
0000:06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:06:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
```

---


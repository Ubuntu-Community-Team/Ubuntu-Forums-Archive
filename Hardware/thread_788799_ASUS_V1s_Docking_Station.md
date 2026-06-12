---
title: "ASUS V1s Docking Station"
date: 2008-05-10
forum: Hardware
---

### Post by zoku88 on 2008-05-10
Hey

I'm having problems getting my docking station to work correctly with my laptop.  All of the USB devices are recognized, but I can't use the audio jacks on it or the external monitor hooked up via the DVI port.

I'm not sure how exactly the docking station interfaces with the laptop,'but if it's PCI, I guess it will be list below (lspci)

Thanks in advance 

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
05:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff
```

---

### Post by zoku88 on 2008-05-10
Oh, I forgot to mention that I'm on 8.04 atm.

---

### Post by imkebe on 2008-10-09
There's no way to use sound on external screen via DVI! DVI - Digital Visual Interface - no sound there.
You can use builtin HDMI port,or just use sounds output on dock station.

You can chceck also some solutions refered to Asus V1S on [https://wiki.ubuntu.com/LaptopTestingTeam/AsusV1S](https://wiki.ubuntu.com/LaptopTestingTeam/AsusV1S)

---


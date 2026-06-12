---
title: "eSATA not autodetected...no errors"
date: 2010-01-11
forum: Hardware
---

### Post by nathanhillinbl on 2010-01-11
I'm running Kubuntu 9.10 on an Asus G51VX laptop with a 1Tb Fantom eSATA HDD (formatted to ext3, I believe), which is not auto-detected upon hotplugging or boot. 

What info can I provide to get some help with this?

Thanks in advance,
Nate

---

### Post by ibninja on 2010-01-11
please post the output of 
```
fdisk -l
```
and
```
lspci
```
when run in terminal.

---

### Post by nathanhillinbl on 2010-01-11
fdisk -l outputs nothing while lspci outputs:
```
nate@monte:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                   
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)                                                                
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)                                                                  
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)                                                                  
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)                                                                  
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260M] (rev a2)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
nate@monte:~$

```

---

### Post by ibninja on 2010-01-11
Does the partitions file in /proc/ change any when you plug it in? (it may take a moment, but gedit should tell you it changed in about a minute if it's going to change) (this is roughly equivalent to fdisk -l, but less likely to fail)

---

### Post by nathanhillinbl on 2010-01-11
Nope, didn't change at all. Thanks for the reply!

---

### Post by nathanhillinbl on 2010-01-11
I decided to get it over and do my 300Gb home folder transfer via USB (Takes forever!), but it would still be nice to have this working for the future.

---

### Post by ibninja on 2010-01-11
Is there an option in your BIOS to set SATA to legacy support mode?

---

### Post by nathanhillinbl on 2010-01-11
> **ibninja said:**
> Is there an option in your BIOS to set SATA to legacy support mode?

Frankly, my BIOS seems quite limited and locked down to me. It's basically boot preferences, with a few extra settings. I'll take a look once the USB transfer finishes.

---


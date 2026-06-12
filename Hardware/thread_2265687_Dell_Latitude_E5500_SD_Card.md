---
title: "Dell Latitude E5500 SD Card"
date: 2015-02-17
forum: Hardware
---

### Post by tada-jin on 2015-02-17
hi all, new ish to ubuntu.

i have a bog standard Dell E5500 laptop, and for some reason the SD card does not work. and it didnt work in windows either.

Anyone have an idea?

Thanks in advance.

---

### Post by coldraven on 2015-02-17
You could try running lsusb with a card in the slot
```
lsusb
```

On my laptop it looks like this. Without a card in the slot the top line is missing.
```
 lsusb
Bus 001 Device 008: ID 03f0:0423 Hewlett-Packard HS-COMBO Cardreader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 09da:000a A4 Tech Co., Ltd Optical Mouse Opto 510D
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```
To find out what version of Ubuntu you are running use:
```
cat /etc/*-release
```
Did you try with any other cards?
It could just be that someone jammed a card into the slot and bent the contacts

---

### Post by efflandt on 2015-02-17
After inserting an SD card run **dmesg** from a terminal and see what the tail end of that shows. Also try **sudo fdisk -l** (small L) In some cases the built-in memory card slot is not internally USB connected, but some other block device. So besides **lsusb**, you might see if **lspci** shows anything about the memory card device. Or it may depend what filesystem is on the card if something formatted it other than FAT32.

---

### Post by tada-jin on 2015-02-17
> **efflandt said:**
> After inserting an SD card run **dmesg** from a terminal and see what the tail end of that shows. Also try **sudo fdisk -l** (small L) In some cases the built-in memory card slot is not internally USB connected, but some other block device. So besides **lsusb**, you might see if **lspci** shows anything about the memory card device. Or it may depend what filesystem is on the card if something formatted it other than FAT32.

**lspci **showed this:
Latitude-E5500:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
**02:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)**
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Intel Corporation WiFi Link 5100

it sees it, but for some reason, nothing shows when i have a known working card in it. i have looked to see if there is any bent pins, etc, and i cant see anything wrong.

EDIT: i am running Ubuntu 14.10

---

### Post by coldraven on 2015-02-21
Is it an elderly machine? Try using an old card that is just regular SD and not SDHC.

---

### Post by tada-jin on 2015-03-02
its only a 2gb SD, deffinatly not SDHC

---


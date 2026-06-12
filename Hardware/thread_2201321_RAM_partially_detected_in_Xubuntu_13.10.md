---
title: "RAM partially detected in Xubuntu 13.10"
date: 2014-01-23
forum: Hardware
---

### Post by paco3 on 2014-01-23
I installed Xubuntu 13.10 in my old reliable Compaq Presario v3000 [AMD 64, Kernel: Linux 3.11.0-15-generic (x86_64)]. It's very nice but the performance is poor, specially with Firefox. I checked system monitor and **it only detects 925,9 MiB of RAM and I have 2 GB**. What can I do? This is the _lspci_ output:
[INDENT=2][SIZE=2]00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce Go 6150] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: NVIDIA Corporation MCP51 PMU (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)[/SIZE]
[/INDENT]

---

### Post by mikewhatever on 2014-01-23
...and why do you think there is a RAM problem? The output you posted might be useful elsewhere, but how is it related to your question?

---

### Post by mörgæs on 2014-01-24
Please post the output of **free -m**.

---

### Post by paco3 on 2014-01-24
I checked the BIOS and I had only 1GB so one of the cards is damaged. Thank you for your time and sorry about my "rookieness". :oops:

---

### Post by Bucky Ball on 2014-01-24
All good. Please mark as solved by following the instructions in my signature. Thanks. ;)

---


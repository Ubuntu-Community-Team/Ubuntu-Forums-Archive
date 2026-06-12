---
title: "Card Reader Not Working with Dell 1501 running Feisty Beta"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by redDEADresolve on 2007-04-07
I'm running the feisty beta on my dell 1501 laptop which has a ricoh 3-in-1 card reader built in, unfortunately it's not working in Feisty. It did work in Edgy Eft. Any ideas on whats up? It's the only thing not working in Feisty on the Dell 1501.


red@red-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)

---

### Post by redDEADresolve on 2007-04-08
red@red-laptop:~$ lsmod | grep sd
sdhci                  18700  0 
mmc_core               26756  1 sdhci
tsdev                   8768  0 
sd_mod                 23428  3 
scsi_mod              142348  3 sg,sd_mod,libata

---

### Post by jpeddicord on 2007-04-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88992](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88992) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is a regression. I have an E1505 with the same Ricoh card reader, and up until a few weeks ago, it worked perfectly.

The bug is currently listed as In Progress, so it will probably be resolved in the coming weeks. Keep your system up to date until then!

Jacob

---

### Post by whitesox on 2007-04-11
Its working, just not detected.  To quote a post on the bug mailing list:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96870/comments/11]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96870/comments/11")
> I recently experienced the same regression with my Ricoh card reader. I should add that the device is being created successfully. It's just not being mounted automatically. 'sudo mount /dev/mmcblk0p1 /mnt' allows me to access my data on my SD card.

---


---
title: "RAID/disk array card problem with identifying disks"
date: 2020-10-19
forum: Hardware
---

### Post by alex346 on 2020-10-19
Hello,
I have lot of disks in my computer - disks has different age and condition.
I have a problems in syslog(dmesg-T output below).

I have IBM/LENOVO RAID controlled named 1068E, but probably with changed firmware to normal controller - I see all 8 disks connected to it as normal drives like sda,sdb, etc. I also can read smartctl in normal way (through smartctl -a /dev/sda).

I am attaching output from lspci command, problematic controller is that one:
07:00.0 SCSI storage controller: Broadcom / LSI SAS1068E PCI-Express Fusion-MPT SAS (rev 08)

Is that possible to talk to that controller through megacli or any other command to get information about disks?
So, but I am really unsure, if that I have RAID controller or only SATA expansion card :)
[B]But if you would like to my syslog output - there are many errors which are not easy understable for me, and I can't investigate which drive is problemmatic one.
[/B]
```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d0)
00:1c.4 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 5 (rev d0)
00:1c.6 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 7 (rev d0)
00:1c.7 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 8 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation H97 Chipset LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev e7)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 04)
05:01.0 RAID bus controller: Promise Technology, Inc. PDC40719 [FastTrak TX4300/TX4310] (rev 02)
06:00.0 RAID bus controller: Broadcom / LSI MegaRAID SAS 2108 [Liberator] (rev 03)
**07:00.0 SCSI storage controller: Broadcom / LSI SAS1068E PCI-Express Fusion-MPT SAS (rev 08)**
08:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)

```



```
[pon pa&#378; 19 05:24:04 2020] ata8.00: exception Emask 0x10 SAct 0x80000 SErr 0x400100 action 0x6 frozen[pon pa&#378; 19 05:24:04 2020] ata8.00: irq_stat 0x08000000, interface fatal error
[pon pa&#378; 19 05:24:04 2020] ata8: SError: { UnrecovData Handshk }
[pon pa&#378; 19 05:24:04 2020] ata8.00: failed command: WRITE FPDMA QUEUED
[pon pa&#378; 19 05:24:04 2020] ata8.00: cmd 61/e0:98:00:08:46/01:00:5d:01:00/40 tag 19 ncq dma 245760 out
                                     res 40/00:98:00:08:46/00:00:5d:01:00/40 Emask 0x10 (ATA bus error)
[pon pa&#378; 19 05:24:04 2020] ata8.00: status: { DRDY }
[pon pa&#378; 19 05:24:04 2020] ata8: hard resetting link
[pon pa&#378; 19 05:24:04 2020] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[pon pa&#378; 19 05:24:04 2020] ata8.00: configured for UDMA/133
[pon pa&#378; 19 05:24:04 2020] ata8: EH complete
[pon pa&#378; 19 05:24:04 2020] ata8.00: exception Emask 0x10 SAct 0x4800000 SErr 0x400100 action 0x6 frozen
[pon pa&#378; 19 05:24:04 2020] ata8.00: irq_stat 0x08000000, interface fatal error
[pon pa&#378; 19 05:24:04 2020] ata8: SError: { UnrecovData Handshk }
[pon pa&#378; 19 05:24:04 2020] ata8.00: failed command: READ FPDMA QUEUED
[pon pa&#378; 19 05:24:04 2020] ata8.00: cmd 60/08:b8:d0:1d:05/00:00:e0:01:00/40 tag 23 ncq dma 4096 in
                                     res 40/00:d0:00:08:46/00:00:5d:01:00/40 Emask 0x10 (ATA bus error)
[pon pa&#378; 19 05:24:04 2020] ata8.00: status: { DRDY }
[pon pa&#378; 19 05:24:04 2020] ata8.00: failed command: WRITE FPDMA QUEUED
[pon pa&#378; 19 05:24:04 2020] ata8.00: cmd 61/e0:d0:00:08:46/01:00:5d:01:00/40 tag 26 ncq dma 245760 out
                                     res 40/00:d0:00:08:46/00:00:5d:01:00/40 Emask 0x10 (ATA bus error)
[pon pa&#378; 19 05:24:04 2020] ata8.00: status: { DRDY }
[pon pa&#378; 19 05:24:04 2020] ata8: hard resetting link
[pon pa&#378; 19 05:24:05 2020] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[pon pa&#378; 19 05:24:05 2020] ata8.00: configured for UDMA/133
[pon pa&#378; 19 05:24:05 2020] ata8: EH complete
[pon pa&#378; 19 05:24:05 2020] ata8.00: exception Emask 0x10 SAct 0x3000 SErr 0x400100 action 0x6 frozen
[pon pa&#378; 19 05:24:05 2020] ata8.00: irq_stat 0x08000000, interface fatal error
[pon pa&#378; 19 05:24:05 2020] ata8: SError: { UnrecovData Handshk }
[pon pa&#378; 19 05:24:05 2020] ata8.00: failed command: WRITE FPDMA QUEUED
[pon pa&#378; 19 05:24:05 2020] ata8.00: cmd 61/e0:60:00:08:46/01:00:5d:01:00/40 tag 12 ncq dma 245760 out
                                     res 40/00:68:d0:1d:05/00:00:e0:01:00/40 Emask 0x10 (ATA bus error)
[pon pa&#378; 19 05:24:05 2020] ata8.00: status: { DRDY }
[pon pa&#378; 19 05:24:05 2020] ata8.00: failed command: READ FPDMA QUEUED
[pon pa&#378; 19 05:24:05 2020] ata8.00: cmd 60/08:68:d0:1d:05/00:00:e0:01:00/40 tag 13 ncq dma 4096 in
                                     res 40/00:68:d0:1d:05/00:00:e0:01:00/40 Emask 0x10 (ATA bus error)
[pon pa&#378; 19 05:24:05 2020] ata8.00: status: { DRDY }
[pon pa&#378; 19 05:24:05 2020] ata8: hard resetting link
[pon pa&#378; 19 05:24:05 2020] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[pon pa&#378; 19 05:24:05 2020] ata8.00: configured for UDMA/133
[pon pa&#378; 19 05:24:05 2020] ata8: EH complete
[pon pa&#378; 19 05:24:05 2020] ata8: limiting SATA link speed to 3.0 Gbps
[pon pa&#378; 19 05:24:05 2020] ata8.00: exception Emask 0x10 SAct 0x3000 SErr 0x400100 action 0x6 frozen
[pon pa&#378; 19 05:24:05 2020] ata8.00: irq_stat 0x08000000, interface fatal error
[pon pa&#378; 19 05:24:05 2020] ata8: SError: { UnrecovData Handshk }
[pon pa&#378; 19 05:24:05 2020] ata8.00: failed command: READ FPDMA QUEUED
[pon pa&#378; 19 05:24:05 2020] ata8.00: cmd 60/08:60:d0:1d:05/00:00:e0:01:00/40 tag 12 ncq dma 4096 in
                                     res 40/00:68:00:08:46/00:00:5d:01:00/40 Emask 0x10 (ATA bus error)
[pon pa&#378; 19 05:24:05 2020] ata8.00: status: { DRDY }
[pon pa&#378; 19 05:24:05 2020] ata8.00: failed command: WRITE FPDMA QUEUED
[pon pa&#378; 19 05:24:05 2020] ata8.00: cmd 61/e0:68:00:08:46/01:00:5d:01:00/40 tag 13 ncq dma 245760 out
                                     res 40/00:68:00:08:46/00:00:5d:01:00/40 Emask 0x10 (ATA bus error)
[pon pa&#378; 19 05:24:05 2020] ata8.00: status: { DRDY }
[pon pa&#378; 19 05:24:05 2020] ata8: hard resetting link
[pon pa&#378; 19 05:24:05 2020] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[pon pa&#378; 19 05:24:05 2020] ata8.00: configured for UDMA/133
[pon pa&#378; 19 05:24:05 2020] ata8: EH complete
[pon pa&#378; 19 05:30:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 05:30:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 05:40:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 05:40:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 05:50:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 05:50:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:00:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:00:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:10:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:10:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:20:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:20:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:30:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:30:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:40:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:40:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:50:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 06:50:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:00:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:00:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:10:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:10:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:20:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:20:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:30:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:30:46 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:40:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:40:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:50:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 07:50:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:00:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:00:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:10:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:10:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:20:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:20:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:30:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:30:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:40:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:40:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:50:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 08:50:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:00:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:00:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:10:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:10:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:20:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:20:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:30:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:30:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:40:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:40:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:50:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 09:50:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 10:00:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 10:00:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 10:10:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 10:10:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 10:20:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 10:20:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply
[pon pa&#378; 19 10:30:47 2020] mptbase: ioc0: LogInfo(0x30030108): Originator={IOP}, Code={Invalid Page}, SubCode(0x0108) cb_idx mptctl_reply



```

---

### Post by TheFu on 2020-10-21
Usually, the SMART data will have all the disk errors enumerated. Check that first.  For HBAs, the best answer is to move a disk one-at-a-time to a different controller and see if that disk shows the same problem.

For storage systems step to use LVM or mdadm sw-RAID, changing the HBA doesn't matter.  But if an HBA is providing HW-RAID, then the only answer is to get an identical make and model and "lot" of the HBA, load the exact same firmware and swap it.  Before doing that, I'd replace all the cables.

Keep track, carefully, of all changes made, so you can track which errors  follow a change.

---


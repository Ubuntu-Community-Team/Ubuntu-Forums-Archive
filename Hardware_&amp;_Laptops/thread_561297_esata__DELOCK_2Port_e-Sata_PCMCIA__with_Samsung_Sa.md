---
title: "esata  DELOCK 2Port e-Sata PCMCIA  with Samsung Sata HDD"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by blaufotograph on 2007-09-27
Hello @All,

i have the following problem with my DELOCK 2Port e-Sata PCMCIA  Card and my Samsung 500GB Sata HDD:

If i mount my external Harddisk (built-in in an IcyBox with USB and e-Sata Port) with the USB Cable everything is fine. It is working without any problems.

But if i connect my harddisk with the Delock eSata PCMCIA Cardbus Adapter it could be that i'm not able to write or read from my disk. Especially the issue occurs whether i copy a lot of little files.
The communication and copying stops for a while, you can see the messages in /var/log/messages like below. Maybe in some seconds the drive will work, but very often the drive and copying from the data do hang.

I have Kubuntu 7.04 (german) with the actual kernel ...

uname -a
Linux UBUNTUNB 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

For infomation i give you the output from lspci, and the log messages from /var/log/messages.

Yes of course i used google very intensively!
Please give me help. I will appreciate this.

i am using the sata_sil module

Output lspci:
------------------------------------------
abirndt@UBUNTUNB:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
04:00.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

--------------------------------------------

if the issue occurs, the following messages comes in /var/log/messages:
---------------------------------------------
Sep 27 17:38:35 UBUNTUNB kernel: [37977.820000] ata4: hard resetting port
Sep 27 17:38:35 UBUNTUNB kernel: [37978.544000] ata4: SATA link down (SStatus 0 SControl 310)
Sep 27 17:38:35 UBUNTUNB kernel: [37978.544000] ata4: failed to recover some devices, retrying in 5 secs





Sep 27 17:38:40 UBUNTUNB kernel: [37983.548000] ata4: hard resetting port
Sep 27 17:38:41 UBUNTUNB kernel: [37984.272000] ata4: SATA link down (SStatus 0 SControl 310)
Sep 27 17:38:41 UBUNTUNB kernel: [37984.272000] ata4.00: limiting speed to UDMA/100:PIO3
Sep 27 17:38:41 UBUNTUNB kernel: [37984.272000] ata4: failed to recover some devices, retrying in 5 secs
Sep 27 17:38:43 UBUNTUNB kernel: [37986.444000] usb 4-1: USB disconnect, address 9
Sep 27 17:38:43 UBUNTUNB kernel: [37986.556000] usb 4-1: new low speed USB device using uhci_hcd and address 10
Sep 27 17:38:44 UBUNTUNB kernel: [37986.728000] usb 4-1: configuration #1 chosen from 1 choice
Sep 27 17:38:44 UBUNTUNB kernel: [37986.744000] input: Logitech Optical USB Mouse as /class/input/input16
Sep 27 17:38:44 UBUNTUNB kernel: [37986.744000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.3-1
Sep 27 17:38:46 UBUNTUNB kernel: [37989.276000] ata4: hard resetting port
Sep 27 17:38:47 UBUNTUNB kernel: [37990.156000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:38:47 UBUNTUNB kernel: [37990.180000] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:38:47 UBUNTUNB kernel: [37990.188000] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:38:47 UBUNTUNB kernel: [37990.188000] ata4.00: configured for UDMA/100
Sep 27 17:38:47 UBUNTUNB kernel: [37990.188000] ata4: EH pending after completion, repeating EH (cnt=4)
Sep 27 17:38:48 UBUNTUNB kernel: [37990.904000] ata4: soft resetting port
Sep 27 17:38:48 UBUNTUNB kernel: [37991.060000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:38:48 UBUNTUNB kernel: [37991.068000] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] ata4.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] ata4.00: configured for UDMA/100
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] ata4: EH complete
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] sdb: Write Protect is off
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] sdb: Write Protect is off
Sep 27 17:38:48 UBUNTUNB kernel: [37991.076000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:40:40 UBUNTUNB kernel: [38102.964000] pccard: card ejected from slot 0
Sep 27 17:40:40 UBUNTUNB kernel: [38103.000000] ata4.00: disabled
Sep 27 17:40:40 UBUNTUNB kernel: [38103.000000] Synchronizing SCSI cache for disk sdb:
Sep 27 17:40:40 UBUNTUNB kernel: [38103.004000] FAILED
Sep 27 17:40:40 UBUNTUNB kernel: [38103.004000]   status = 0, message = 00, host = 4, driver = 00
Sep 27 17:40:40 UBUNTUNB kernel: [38103.004000]   <6>ACPI: PCI interrupt for device 0000:04:00.0 disabled


Sep 27 17:51:57 UBUNTUNB kernel: [38780.528000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 27 17:51:58 UBUNTUNB kernel: [38780.840000] ata6: soft resetting port
Sep 27 17:51:58 UBUNTUNB kernel: [38780.996000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:51:58 UBUNTUNB kernel: [38781.004000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:51:58 UBUNTUNB kernel: [38781.012000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:51:58 UBUNTUNB kernel: [38781.012000] ata6.00: configured for UDMA/100
Sep 27 17:51:58 UBUNTUNB kernel: [38781.012000] ata6: EH complete
Sep 27 17:51:58 UBUNTUNB kernel: [38781.024000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:51:58 UBUNTUNB kernel: [38781.024000] sdb: Write Protect is off
Sep 27 17:51:58 UBUNTUNB kernel: [38781.024000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:52:29 UBUNTUNB kernel: [38811.828000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 27 17:52:29 UBUNTUNB kernel: [38812.140000] ata6: soft resetting port
Sep 27 17:52:29 UBUNTUNB kernel: [38812.296000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:52:29 UBUNTUNB kernel: [38812.320000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:29 UBUNTUNB kernel: [38812.328000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:29 UBUNTUNB kernel: [38812.328000] ata6.00: configured for UDMA/100
Sep 27 17:52:29 UBUNTUNB kernel: [38812.328000] ata6: EH complete
Sep 27 17:52:29 UBUNTUNB kernel: [38812.336000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:52:29 UBUNTUNB kernel: [38812.336000] sdb: Write Protect is off
Sep 27 17:52:29 UBUNTUNB kernel: [38812.340000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:52:30 UBUNTUNB kernel: [38812.952000]          res 51/00:00:0e:00:00/00:00:00:00:00/ee Emask 0x1 (device error)
Sep 27 17:52:30 UBUNTUNB kernel: [38813.248000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:30 UBUNTUNB kernel: [38813.256000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:30 UBUNTUNB kernel: [38813.256000] ata6.00: configured for UDMA/100
Sep 27 17:52:30 UBUNTUNB kernel: [38813.256000] ata6: EH complete
Sep 27 17:52:30 UBUNTUNB kernel: [38813.376000]          res 51/00:00:0e:00:00/00:00:00:00:00/ee Emask 0x1 (device error)
Sep 27 17:52:30 UBUNTUNB kernel: [38813.384000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:30 UBUNTUNB kernel: [38813.392000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:30 UBUNTUNB kernel: [38813.392000] ata6.00: configured for UDMA/100
Sep 27 17:52:30 UBUNTUNB kernel: [38813.392000] ata6: EH complete
Sep 27 17:52:30 UBUNTUNB kernel: [38813.392000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:52:30 UBUNTUNB kernel: [38813.404000] sdb: Write Protect is off
Sep 27 17:52:30 UBUNTUNB kernel: [38813.408000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:52:30 UBUNTUNB kernel: [38813.412000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:52:30 UBUNTUNB kernel: [38813.412000] sdb: Write Protect is off
Sep 27 17:52:30 UBUNTUNB kernel: [38813.416000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:52:30 UBUNTUNB kernel: [38813.600000] ata6.00: limiting speed to UDMA/66:PIO4
Sep 27 17:52:30 UBUNTUNB kernel: [38813.600000]          res ff/ff:ff:ff:ff:ff/ff:ff:ff:ff:ff/ff Emask 0x2 (HSM violation)
Sep 27 17:52:31 UBUNTUNB kernel: [38813.912000] ata6: soft resetting port
Sep 27 17:52:31 UBUNTUNB kernel: [38814.068000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:53:01 UBUNTUNB kernel: [38844.076000] ata6.00: qc timeout (cmd 0xec)
Sep 27 17:53:01 UBUNTUNB kernel: [38844.076000] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 27 17:53:01 UBUNTUNB kernel: [38844.076000] ata6: failed to recover some devices, retrying in 5 secs
Sep 27 17:53:06 UBUNTUNB kernel: [38849.080000] ata6: hard resetting port
Sep 27 17:53:07 UBUNTUNB kernel: [38849.556000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:53:07 UBUNTUNB kernel: [38849.580000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168

Sep 27 17:51:57 UBUNTUNB kernel: [38780.528000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 27 17:51:58 UBUNTUNB kernel: [38780.840000] ata6: soft resetting port
Sep 27 17:51:58 UBUNTUNB kernel: [38780.996000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:51:58 UBUNTUNB kernel: [38781.004000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:51:58 UBUNTUNB kernel: [38781.012000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:51:58 UBUNTUNB kernel: [38781.012000] ata6.00: configured for UDMA/100
Sep 27 17:51:58 UBUNTUNB kernel: [38781.012000] ata6: EH complete
Sep 27 17:51:58 UBUNTUNB kernel: [38781.024000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:51:58 UBUNTUNB kernel: [38781.024000] sdb: Write Protect is off
Sep 27 17:51:58 UBUNTUNB kernel: [38781.024000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:52:29 UBUNTUNB kernel: [38811.828000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 27 17:52:29 UBUNTUNB kernel: [38812.140000] ata6: soft resetting port
Sep 27 17:52:29 UBUNTUNB kernel: [38812.296000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:52:29 UBUNTUNB kernel: [38812.320000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:29 UBUNTUNB kernel: [38812.328000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:29 UBUNTUNB kernel: [38812.328000] ata6.00: configured for UDMA/100
Sep 27 17:52:29 UBUNTUNB kernel: [38812.328000] ata6: EH complete
Sep 27 17:52:29 UBUNTUNB kernel: [38812.336000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:52:29 UBUNTUNB kernel: [38812.336000] sdb: Write Protect is off
Sep 27 17:52:29 UBUNTUNB kernel: [38812.340000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:52:30 UBUNTUNB kernel: [38812.952000]          res 51/00:00:0e:00:00/00:00:00:00:00/ee Emask 0x1 (device error)
Sep 27 17:52:30 UBUNTUNB kernel: [38813.248000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:30 UBUNTUNB kernel: [38813.256000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:30 UBUNTUNB kernel: [38813.256000] ata6.00: configured for UDMA/100
Sep 27 17:52:30 UBUNTUNB kernel: [38813.256000] ata6: EH complete
Sep 27 17:52:30 UBUNTUNB kernel: [38813.376000]          res 51/00:00:0e:00:00/00:00:00:00:00/ee Emask 0x1 (device error)
Sep 27 17:52:30 UBUNTUNB kernel: [38813.384000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:30 UBUNTUNB kernel: [38813.392000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:52:30 UBUNTUNB kernel: [38813.392000] ata6.00: configured for UDMA/100
Sep 27 17:52:30 UBUNTUNB kernel: [38813.392000] ata6: EH complete
Sep 27 17:52:30 UBUNTUNB kernel: [38813.392000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:52:30 UBUNTUNB kernel: [38813.404000] sdb: Write Protect is off
Sep 27 17:52:30 UBUNTUNB kernel: [38813.408000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:52:30 UBUNTUNB kernel: [38813.412000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:52:30 UBUNTUNB kernel: [38813.412000] sdb: Write Protect is off
Sep 27 17:52:30 UBUNTUNB kernel: [38813.416000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:52:30 UBUNTUNB kernel: [38813.600000] ata6.00: limiting speed to UDMA/66:PIO4
Sep 27 17:52:30 UBUNTUNB kernel: [38813.600000]          res ff/ff:ff:ff:ff:ff/ff:ff:ff:ff:ff/ff Emask 0x2 (HSM violation)
Sep 27 17:52:31 UBUNTUNB kernel: [38813.912000] ata6: soft resetting port
Sep 27 17:52:31 UBUNTUNB kernel: [38814.068000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:53:01 UBUNTUNB kernel: [38844.076000] ata6.00: qc timeout (cmd 0xec)
Sep 27 17:53:01 UBUNTUNB kernel: [38844.076000] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 27 17:53:01 UBUNTUNB kernel: [38844.076000] ata6: failed to recover some devices, retrying in 5 secs
Sep 27 17:53:06 UBUNTUNB kernel: [38849.080000] ata6: hard resetting port
Sep 27 17:53:07 UBUNTUNB kernel: [38849.556000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:53:07 UBUNTUNB kernel: [38849.580000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168

Sep 27 17:55:20 UBUNTUNB kernel: [38982.984000] ata6: hard resetting port
Sep 27 17:55:20 UBUNTUNB kernel: [38983.460000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:55:20 UBUNTUNB kernel: [38983.484000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:55:20 UBUNTUNB kernel: [38983.492000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:55:20 UBUNTUNB kernel: [38983.492000] ata6.00: configured for UDMA/66
Sep 27 17:55:20 UBUNTUNB kernel: [38983.492000] ata6: EH complete
Sep 27 17:55:20 UBUNTUNB kernel: [38983.508000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:55:20 UBUNTUNB kernel: [38983.508000] sdb: Write Protect is off
Sep 27 17:55:20 UBUNTUNB kernel: [38983.508000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 27 17:55:21 UBUNTUNB kernel: [38983.644000] ata6.00: limiting speed to UDMA/33:PIO4
Sep 27 17:55:21 UBUNTUNB kernel: [38983.644000]          res ff/ff:ff:ff:ff:ff/00:01:0c:00:00/ff Emask 0x2 (HSM violation)
Sep 27 17:55:21 UBUNTUNB kernel: [38983.956000] ata6: soft resetting port
Sep 27 17:55:21 UBUNTUNB kernel: [38984.112000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:55:51 UBUNTUNB kernel: [39014.112000] ata6.00: qc timeout (cmd 0xec)
Sep 27 17:55:51 UBUNTUNB kernel: [39014.112000] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 27 17:55:51 UBUNTUNB kernel: [39014.112000] ata6: failed to recover some devices, retrying in 5 secs
Sep 27 17:55:56 UBUNTUNB kernel: [39019.116000] ata6: hard resetting port
Sep 27 17:55:56 UBUNTUNB kernel: [39019.592000] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 27 17:55:56 UBUNTUNB kernel: [39019.600000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:55:56 UBUNTUNB kernel: [39019.608000] ata6.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Sep 27 17:55:56 UBUNTUNB kernel: [39019.608000] ata6.00: configured for UDMA/33
Sep 27 17:55:56 UBUNTUNB kernel: [39019.608000] ata6: EH complete
Sep 27 17:55:56 UBUNTUNB kernel: [39019.620000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
Sep 27 17:55:56 UBUNTUNB kernel: [39019.620000] sdb: Write Protect is off
Sep 27 17:55:56 UBUNTUNB kernel: [39019.624000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by blaufotograph on 2007-09-27
Maybe someone is speaking german:

I tried to get an solution in the german board

[http://forum.ubuntuusers.de/topic/91310/](http://forum.ubuntuusers.de/topic/91310/)

But there was nobody able to help me

Thanks

---

### Post by rmaarsen on 2007-09-28
Hi,

In this topic, no solution was given :( I'm struggling with the same problem.

I've seen topics about the wiring of the disk. Did you try to change the cable? 

Regards, Ruben.

---

### Post by blaufotograph on 2007-09-28
> **rmaarsen said:**
> ....
I've seen topics about the wiring of the disk. Did you try to change the cable? 
....

Hi Ruben,

thank you for your answer. Yes, i changed the cable, i changed the PCMCIA Adapter, and even of course i changed the harddisk. Everytime the same problem.

In my opinion it is a kernel or driver problem with the sata_sil module.
I think you notice, my english is not so perfect, and so it is difficult for me the explain all this with the right word.

Maybe you are able to open an bug report at the ubuntu kernel dev-site? Yes of course i will help you to discuss there and bring logs and anything else what ever they need.

see you
Axel

---

### Post by blaufotograph on 2007-09-28
> **rmaarsen said:**
> ...
In this topic, no solution was given :( I'm struggling with the same problem.
...

Hi Ruben, wich kind of harddisk and PCMCIA Adapter do you use? It is the same like me?

---

### Post by finite9 on 2008-05-29
I have exactly the same errors in /var/log/messages with a ST Labs eSATA CardBus controller.

I use CentOS 5.1 on my server and I connect 2 Western Digital 500GB discs with triple interface connectors to the ST Labs controller.  I can run badblocks on both discs simultaneously for 48 hours with no errors whatsoever, and  can partition and format them create raid array and dmcrypt them and create a partition and mount it.  No issues at all so far.

But then, the discs will spindown into power saving mode, and if I try to access them again after that, I get exactly the same messages as you get, and usually one of the ports "hangs" and the LED for that port stays on constantly, and the only solution is to unplug the CardBus adapter and completely disconnect power from the disc drive.

I also get the same hanging during boot more oftan than not.

I have compiled the latest kernel (2.6.25) with the very latest sil_sata driver and I still get "hard resetting port" and "no response giving up" messages.

I have not tried with Windows yet to completely rule out the possiblity of hardware failure (if it works in Windows then its an issue with the sil_sata driver, if it fails in same way it's a duff controller).

I have search a lot on Google but it seems there are very few people with eSATA Cardbus controllers and eSATA drives :(

---


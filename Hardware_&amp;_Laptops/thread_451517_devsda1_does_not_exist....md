---
title: "/dev/sda1 does not exist..."
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by trojahn on 2007-05-22
Hello, 

It's my first time with Ubuntu but I have a little experience with linux in general... This problem, tho, is driving me crazy...

I have 2 ATA HDDs... The 1st IDE has my WinXP system, the 2nd IDE has the linux and another NTFS partition... The 2nd IDE works fine under Ubuntu, it even auto-mounted my NTFS partition...

The 1st HDD throws alot of error messages on DMESG on boot which I'm not able to understand... Here's an example:

[   26.413054] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   26.413062] ata1.00: ATA-6: WDC WD800BB-00JHA0, 05.01C05, max UDMA/100
[   26.413065] ata1.00: 156301488 sectors, multi 16: LBA 
[   26.421030] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   26.421033] ata1.00: configured for UDMA/100
[   26.421051] scsi1 : pata_sis
[   26.748873] ata2.00: ata_hpa_resize 1: sectors = 117304992, hpa_sectors = 117304992
[   26.748880] ata2.00: ATA-6: SAMSUNG SV0602H, RH100-15, max UDMA/100
[   26.748883] ata2.00: 117304992 sectors, multi 16: LBA 
[   26.748887] ata2.01: ATAPI, max UDMA/33
[   26.756858] ata2.00: ata_hpa_resize 1: sectors = 117304992, hpa_sectors = 117304992
[   26.756861] ata2.00: configured for UDMA/100
[   26.920752] ata2.01: configured for UDMA/33
[   26.920963] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-00JH 05.0 PQ: 0 ANSI: 5
[   26.921570] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SV0602H  RH10 PQ: 0 ANSI: 5
[   26.925569] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL12 PQ: 0 ANSI: 5
[   26.930700] PCI: Enabling device 0000:00:09.0 (0004 -> 0007)
[   26.930722] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 18
[   26.931330] eth0: RealTek RTL8139 at 0xf0822000, 00:02:2a:dc:0b:32, IRQ 18
[   26.931333] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   26.934492] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   26.935088] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 19
[   26.935103] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[   26.935112] 0000:00:0a.0: 3Com PCI 3c905C Tornado at f0848000.
[   26.979549] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   26.979627] sda: Write Protect is off
[   26.979630] sda: Mode Sense: 00 3a 00 00
[   26.979655] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.979754] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   26.979765] sda: Write Protect is off
[   26.979767] sda: Mode Sense: 00 3a 00 00
[   26.979782] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.979786]  sda:<3>ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   26.991273] ata1.00: (BMDMA stat 0x24)
[   26.991283] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   26.991284]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   26.991312] ata1: soft resetting port
[   27.152710] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   27.160743] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   27.160747] ata1.00: configured for UDMA/100
[   27.160766] ata1: EH complete
[   27.166032] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   27.166036] ata1.00: (BMDMA stat 0x24)
[   27.166042] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[   27.166044]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   27.166064] ata1: soft resetting port
[   27.328618] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   27.336594] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   27.336597] ata1.00: configured for UDMA/100
[   27.336621] ata1: EH complete

This errors repeat a few times till the system apparently give up trying to mount the unit...

Later when Ubuntu is already running, "fdisk -l" says:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9728    62782020    f  W95 Ext'd (LBA)
/dev/sda5            1913        9728    62781988+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+  82  Linux swap / Solaris
/dev/sdb2            1276        7300    48395812+   f  W95 Ext'd (LBA)
/dev/sdb3              63        1275     9743422+  83  Linux
/dev/sdb5            1276        7300    48395781    7  HPFS/NTFS

Partition table entries are not in disk order

But if I try, "mount -t ntfs /dev/sda1 /media/sda1" I get:
mount: special device /dev/sda1 does not exist

And it really doesn't:
ls /dev/sd* -l
brw-rw---- 1 root disk 8,  0 2007-05-22 06:04 /dev/sda
brw-rw---- 1 root disk 8, 16 2007-05-22 06:04 /dev/sdb
brw-rw---- 1 root disk 8, 17 2007-05-22 06:04 /dev/sdb1
brw-rw---- 1 root disk 8, 19 2007-05-22 06:04 /dev/sdb3
brw-rw---- 1 root disk 8, 21 2007-05-22 06:04 /dev/sdb5

or...ls /dev/disk/by-id/ -l
total 0
lrwxrwxrwx 1 root root  9 2007-05-22 06:04 scsi-1ATA_SAMSUNG_SV0602H_0451J1BW404545 -> ../../sdb
lrwxrwxrwx 1 root root 10 2007-05-22 06:04 scsi-1ATA_SAMSUNG_SV0602H_0451J1BW404545-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-05-22 06:04 scsi-1ATA_SAMSUNG_SV0602H_0451J1BW404545-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 2007-05-22 06:04 scsi-1ATA_SAMSUNG_SV0602H_0451J1BW404545-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 2007-05-22 06:04 scsi-1ATA_WDC_WD800BB-00JHA0_WD-WCAM91071458 -> ../../sda

So, anyone has any clue what's happening here? I literally tried everything I know on this :(

---

### Post by lintoolman on 2007-05-22
Can you mount the drive with "ntfs-3g?"  This is the program I use to mount ntfs partitions.

---

### Post by trojahn on 2007-05-28
Yeah... I did...

After a little research about udev itself, I discovered the partitions weren't being mount coz my flat cable!! As crazy as it sounds (at least to me), changing the flat cable allowed DMA mode 5 to work and it was automatically mounted after that...

Well... Learning every day :)

---


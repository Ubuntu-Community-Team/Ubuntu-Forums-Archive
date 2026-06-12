---
title: "Flash drive not automounting"
date: 2012-05-12
forum: Hardware
---

### Post by carwe on 2012-05-12
Hi,

I have two identical flash drives, SanDisk 16GB. After the purchase they have been used differently though, they have been formatted to different file systems, I added a boot record to one of them and others.

One of them works perfectly, once I plug it in, its folder is opened. Plugging in the other however does not show its folder and also it doesn't appear in /media/. When I insert it, for about 10 seconds its LED flashes and during that time the CPU for the compiz process goes up to 20-25%. After that, the LED is solid red (normal) and the CPU for compiz is normal again. But the drive doesn't show up.

There is some read-only sector from SanDisk pre-installed, it was still there on the problematic flash drive, I removed it. (Before, a CD drive shows up as well in Windows.) Didn't help. I've tried to format it in Widows both to FAT32 and NTFS (quick format, not low-level), didn't help.

I'm running Ubuntu 12.04 32-bit.

The drive is clearly visible to the system, at least to a part:

dmesg|tail:
```
[185537.622475] scsi13 : usb-storage 2-6:1.0
[185538.621149] scsi 13:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
[185538.623193] sd 13:0:0:0: Attached scsi generic sg2 type 0
[185538.628594] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[185540.871254] sd 13:0:0:0: [sdb] 31715327 512-byte logical blocks: (16.2 GB/15.1 GiB)
[185540.872252] sd 13:0:0:0: [sdb] No Caching mode page present
[185540.872255] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[185540.874121] sd 13:0:0:0: [sdb] No Caching mode page present
[185540.874125] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[185540.875672]  sdb: sdb1
```"sudo fdisk -l" with the flash drive connected:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   317444399   158722168+   7  HPFS/NTFS/exFAT
/dev/sda2       467419136   469518335     1049600    c  W95 FAT32 (LBA)
/dev/sda3       469518704   488397167     9439232    7  HPFS/NTFS/exFAT
/dev/sda4       317444400   467411174    74983387+   5  Extended
/dev/sda5       317448192   333064191     7808000   82  Linux swap / Solaris
/dev/sda6       333075708   467411174    67167733+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 16.2 GB, 16238247424 bytes
16 heads, 32 sectors/track, 61943 cylinders, total 31715327 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31715326    15857647+   7  HPFS/NTFS/exFAT

```"sudo fdisk -l" *without* the flash drive connected:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80d2f3ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   317444399   158722168+   7  HPFS/NTFS/exFAT
/dev/sda2       467419136   469518335     1049600    c  W95 FAT32 (LBA)
/dev/sda3       469518704   488397167     9439232    7  HPFS/NTFS/exFAT
/dev/sda4       317444400   467411174    74983387+   5  Extended
/dev/sda5       317448192   333064191     7808000   82  Linux swap / Solaris
/dev/sda6       333075708   467411174    67167733+  83  Linux

Partition table entries are not in disk order

```Any ideas?

---


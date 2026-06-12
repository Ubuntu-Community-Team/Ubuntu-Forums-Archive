---
title: "Ubuntu 13.04 Sometimes wont boot with external USB drive on"
date: 2013-06-01
forum: Hardware
---

### Post by Bladeforce on 2013-06-01
HI, I am having problems with an external USB enclosure. When it is switched on and I boot it sometimes boots and sometimes doesn't! I always get this error though before it either carrying on or crashing out

Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.966218] scsi 8:0:0:0: Direct-Access     WDC WD20 EARS-00MVWB0          PQ: 0 ANSI: 2 CCS
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.966964] scsi 8:0:0:1: Direct-Access     ST350032 0AS                   PQ: 0 ANSI: 2 CCS
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.967553] sd 8:0:0:0: Attached scsi generic sg5 type 0
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.967830] sd 8:0:0:1: Attached scsi generic sg6 type 0
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.968337] sd 8:0:0:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.970687] sd 8:0:0:1: [sdf] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.972308] sd 8:0:0:0: [sde] Write Protect is off
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.972314] sd 8:0:0:0: [sde] Mode Sense: 00 38 00 00
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.974088] sd 8:0:0:1: [sdf] Write Protect is off
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.974094] sd 8:0:0:1: [sdf] Mode Sense: 00 38 00 00
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.975083] sd 8:0:0:0: [sde] Asking for cache data failed
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.975089] sd 8:0:0:0: [sde] Assuming drive cache: write through
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.976128] sd 8:0:0:1: [sdf] Asking for cache data failed
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.976133] sd 8:0:0:1: [sdf] Assuming drive cache: write through
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.982084] sd 8:0:0:0: [sde] Asking for cache data failed
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.982091] sd 8:0:0:0: [sde] Assuming drive cache: write through
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.983085] sd 8:0:0:1: [sdf] Asking for cache data failed
Jun  1 12:20:39 ade-G41D3C kernel: [ 3380.983090] sd 8:0:0:1: [sdf] Assuming drive cache: write through
Jun  1 12:20:39 ade-G41D3C kernel: [ 3381.022485]  sde: sde1
Jun  1 12:20:39 ade-G41D3C kernel: [ 3381.049860]  sdf: sdf1
Jun  1 12:20:39 ade-G41D3C kernel: [ 3381.055081] sd 8:0:0:0: [sde] Asking for cache data failed
Jun  1 12:20:39 ade-G41D3C kernel: [ 3381.055087] sd 8:0:0:0: [sde] Assuming drive cache: write through
Jun  1 12:20:39 ade-G41D3C kernel: [ 3381.055092] sd 8:0:0:0: [sde] Attached SCSI disk
Jun  1 12:20:39 ade-G41D3C kernel: [ 3381.056087] sd 8:0:0:1: [sdf] Asking for cache data failed
Jun  1 12:20:39 ade-G41D3C kernel: [ 3381.056091] sd 8:0:0:1: [sdf] Assuming drive cache: write through
Jun  1 12:20:39 ade-G41D3C kernel: [ 3381.056095] sd 8:0:0:1: [sdf] Attached SCSI disk
Jun  1 12:20:39 ade-G41D3C ata_id[13009]: HDIO_GET_IDENTITY failed for '/dev/sde': Invalid argument
Jun  1 12:20:39 ade-G41D3C ata_id[13010]: HDIO_GET_IDENTITY failed for '/dev/sdf': Invalid argument
Jun  1 12:20:43 ade-G41D3C kernel: [ 3385.199328] EXT4-fs (sde1): recovery complete
Jun  1 12:20:43 ade-G41D3C kernel: [ 3385.199336] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
Jun  1 12:20:43 ade-G41D3C udisksd[2611]: Mounted /dev/sde1 at /media/ade/Various on behalf of uid 1000

---

### Post by VMC on 2013-06-01
After you boot up without the usb plugged in, then plug it in and after things settle down type the following:

```
sudo fdsik -l
```

---

### Post by Bladeforce on 2013-06-01
I presume you mean sudo fdisk not fdsik? :)

Anyway this is the output:

Disk /dev/sda: 323.9 GB, 323928170496 bytes
255 heads, 63 sectors/track, 39382 cylinders, total 632672208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1cfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   446263295   223130624   83  Linux
/dev/sda3       446263296   581222399    67479552   83  Linux
/dev/sda4       581222400   632670207    25723904   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb50034e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   234440703   117219328   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0fb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   210984959   105491456    7  HPFS/NTFS/exFAT
/dev/sdc2       210984960   768479231   278747136   83  Linux
/dev/sdc3       768479232   976773119   104146944   83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
48 heads, 46 sectors/track, 442379 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb199f2ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   976771071   488384512    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f3c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907028991  1953513472   83  Linux

---


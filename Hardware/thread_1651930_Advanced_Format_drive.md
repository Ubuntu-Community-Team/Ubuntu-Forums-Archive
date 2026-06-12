---
title: "Advanced Format drive"
date: 2010-12-23
forum: Hardware
---

### Post by jusbug on 2010-12-23
please guys, i just got myself seagate Momentus XT 500GB and i want to know if is there a way to tell if my new HDD is an Advanced Format drive.

---

### Post by cascade9 on 2010-12-24
I *think* it is, but seagate is coy about 4K sector drives, and 'Seagate SmartAlign'. Which they say is meant to "dynamically manage each individual miss-alignment condition within the hard drive firmware and without the host computer even knowing" and so people dont have to use an alignment jumper or alignment software.

Sounds good, eh? But then on data sheets seagate says "Be sure to install 4k-aware operating systems, such as windows 7 and macOS, or 4k aware hard drive partitoning utilities"

[http://www.seagate.com/docs/pdf/whitepaper/mb_smartalign_technology_faq.pdf](http://www.seagate.com/docs/pdf/whitepaper/mb_smartalign_technology_faq.pdf)

So Idont know if its using and reporting 4K sectors, or if its using 4K sectors and reporting 512b sectors. :( 

Bloody HDD manufacturers, couldnt they just make life easier for once?

---

### Post by jusbug on 2010-12-24
when i do fdisk -l i got:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbcf2992a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   106498047    53248000    7  HPFS/NTFS
/dev/sda2       106498048   976773119   435137536    5  Extended
/dev/sda5       106500096   868356095   380928000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0baca6b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x051d565e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          64  1953520064   976760000+   7  HPFS/NTFS

Disk /dev/dm-0: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6291456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

---

### Post by cascade9 on 2010-12-25
WEll, its not reporting itself as a 4k drive. I dont know if thats because of smart align, or because the version of fdisk you are using isnt 4k aware.

---


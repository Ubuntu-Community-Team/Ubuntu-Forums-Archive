---
title: "Recover corrupted NTFS with Ubuntu."
date: 2010-02-08
forum: Hardware
---

### Post by hariks0 on 2010-02-08
I have a 250 GB external HD in NTFS. It was used to transport data between my office [Windoze] and home [Ubuntu 9.10]. While doing a reinstall of wxp this HD was attached to the office pc. Now the File system of this External HD is Raw. I am sure that wxp has not formatted this as the result would be only an NTFS disk, not raw. I tried the disk utility in Ubuntu and the it displays that the Disk is healthy.

Is there a way to get the data in this disk back using Ubuntu utilities. I thought I would wait for your replies before formatting.

---

### Post by IcarusR on 2010-02-08
Try testdisk 

[http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download")

---

### Post by hariks0 on 2010-02-15
Now here are the outputs:-

```
hari@Indira:~$ sudo sfdisk -l

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   6373    6374-  51199123+  83  Linux
/dev/sda2       6374   30400   24027  192996877+   f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       6374+  12747    6374-  51199123+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6      12748+  19121    6374-  51199123+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7      29793+  30400     608-   4883728+  82  Linux swap / Solaris
/dev/sda8      19122+  21889    2768-  22233928+  83  Linux
/dev/sda9      21890+  29792    7903-  63480816   83  Linux

Disk /dev/sdb: 5690 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  30399   30400- 244187968+   7  HPFS/NTFS
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

```

Both 'parted' and 'cfdisk' returned error messages. But Gparted recognizes the 250 GB HD as unallocated 43.59 GB.

Also my pc refused to boot with this HD connected via USB. It was not so before. So it seems that after running 'Testdisk' there had been some improvement.

---


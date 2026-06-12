---
title: "Partition table broken"
date: 2012-03-26
forum: Hardware
---

### Post by Azathoth_ on 2012-03-26
Hi everyone,

I have problems with a 16 GB MicroSD card. After formating sometimes to FAT and Ext4 with GParted finally I broke it. I tried to restore it with GParted and TestDisk with no help, now it shows as a 8 MB unallocated space disk with no partitions and a broken MBR.
When I try to use TestDisk it shows me the error "Partition sector doesn't have the endmark 0xAA55" and does not show any partition on a deeper search,
I searched over internet and cannot find how to restore, because it does not show any partition to recover and I cannot write a new MBR because I do not have a MBR backup.
When I try to write the right geometry disk (15768 cylinders, 64 heads and 32 sectors of 615 bytes) it shows a lot of partitions but I cannot save changes or delete/create partitions.
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdd - 16 GB / 15 GiB - CHS 15768 64 32
Current partition structure:
     Partition                  Start        End    Size in sectors

check_FAT: can't read FAT boot sector                                           
Invalid FAT boot sector
 1 * hid. FAT32 LBA       1743070  42 31 3314782  10 20 3218865142
 1 * hid. FAT32 LBA       1743070  42 31 3314782  10 20 3218865142

Warning: Bad starting sector (CHS and LBA don't match)
 2 * Sys=A2               2030495  31 30 3589022   4 24 3191862427

Warning: Bad starting sector (CHS and LBA don't match)
 3 * Sys=1D               1743070  43 31 3314782  11 20 3218865142

Warning: Bad starting sector (CHS and LBA don't match)
    Next
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition
```

Does anyone know have to fix the SD?
Thanks in advance.

---


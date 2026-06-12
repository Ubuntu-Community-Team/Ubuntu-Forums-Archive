---
title: "Will win7 recognise a 300gb fat32 logical partition?"
date: 2011-02-01
forum: Hardware
---

### Post by fasoulas on 2011-02-01
I have a sony vaio e series and i want to partition my hard disk in order to istall ubuntu.

My hard disk is 500gb

Current Partitions :
-windows 7
-recovery
-system reserved

I someone told me that i can install ubuntu in an extented partition along with the swap partition ,in order to work because of the max number of primary partitions.

I was thinking of making another logical partition fat32 that a will save my data and i will be able to access it from both OSes.

-100gb windows
-15gb recovery
-100mb sys.res.

-extended
	22gb ubuntu ,ext4 
	8gb swap ,swap
	300gb data ,fat32

the fat32 partition will be about 300gb and my question is ,will it be recognised by windows 7?

---

### Post by sydbat on 2011-02-01
> **fasoulas said:**
> I have a sony vaio e series and i want to partition my hard disk in order to istall ubuntu.

My hard disk is 500gb

Current Partitions :
-windows 7
-recovery
-system reserved

I someone told me that i can install ubuntu in an extented partition along with the swap partition ,in order to work because of the max number of primary partitions.

I was thinking of making another logical partition fat32 that a will save my data and i will be able to access it from both OSes.

-100gb windows
-15gb recovery
-100mb sys.res.

-extended
	22gb ubuntu ,ext4 
	8gb swap ,swap
	300gb data ,fat32

the fat32 partition will be about 300gb and my question is ,will it be recognised by windows 7?No reason to use FAT32. Just use NTFS.

---

### Post by dandnsmith on 2011-02-01
> **fasoulas said:**
> I have a sony vaio e series and i want to partition my hard disk in order to istall ubuntu.

My hard disk is 500gb

Current Partitions :
-windows 7
-recovery
-system reserved

I someone told me that i can install ubuntu in an extented partition along with the swap partition ,in order to work because of the max number of primary partitions.

I was thinking of making another logical partition fat32 that a will save my data and i will be able to access it from both OSes.

-100gb windows
-15gb recovery
-100mb sys.res.

-extended
	22gb ubuntu ,ext4 
	8gb swap ,swap
	300gb data ,fat32

the fat32 partition will be about 300gb and my question is ,will it be recognised by windows 7?

That arrangement works, and offers the least amount of trouble.
You will have no trouble with putting Ubuntu in a logical partition within an extended partition, and there is no problem with using a 300G FAT data logical partition.
Your biggest problem is likely to be the boot situation - where a lot of the user problems arise.

---

### Post by fasoulas on 2011-02-01
I am asking because i saw on a web page that windows might not recognize fat partitions bigger than 32gb

---

### Post by davidmohammed on 2011-02-01
dont use FAT32 - NTFS is your best bet for both ubuntu and windows 7 to cooperate.

---

### Post by fasoulas on 2011-02-01
> **davidmohammed said:**
> dont use FAT32 - NTFS is your best bet for both ubuntu and windows 7 to cooperate.

Ok thanks for the advice

---

### Post by sydbat on 2011-02-02
> **davidmohammed said:**
> dont use FAT32 - NTFS is your best bet for both ubuntu and windows 7 to cooperate.Hang on...where did I hear that recently...oh ya - [http://ubuntuforums.org/showpost.php?p=10418571&postcount=2](http://ubuntuforums.org/showpost.php?p=10418571&postcount=2) ):P

---

### Post by cascade9 on 2011-02-02
> **fasoulas said:**
> I am asking because i saw on a web page that windows might not recognize fat partitions bigger than 32gb

Sort of- 

> You cannot format a volume larger than 32 gigabytes (GB) in size using the FAT32 file system during the Windows XP installation process. Windows XP can mount and support FAT32 volumes larger than 32 GB (subject to the other limits), but you cannot create a FAT32 volume larger than 32 GB by using the Format tool during Setup. If you need to format a volume that is larger than 32 GB, use the NTFS file system to format it.

[http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)

---


---
title: "Can't write to USB Key Drive"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by darkstaar on 2007-12-31
This isn't so much an Ubuntu issue as a hardware problem. I have a 4GB USB flash drive that can't be altered in any way. 

I can mount it, I can copy files from it, but I can't write to it. I can't delete or alter the partition in any way either through Gparted or parted. Dosfsck shows many errors but can't correct them.

Any ideas on how I might be able to recover the use of this miserable flash drive in Ubuntu (I don't run Windows) before I crush it beneath my boot?

---

### Post by Yellow Pasque on 2007-12-31
How are you mounting it? Are you sure that you're mounting with read/write access?

---

### Post by darkstaar on 2007-12-31
I have read/write access. Everything seems to point to a fat32 filesystem gone bad.

---

### Post by Sef on 2007-12-31
I have been having the same problem.  Check out my [thread]("http://ubuntuforums.org/showthread.php?t=618166") for ideas for solving this problem that I still have.

---

### Post by darkstaar on 2007-12-31
@Sef

I Read the thread. Did a fdisk -l on it. The output was nothing like it should be. Still, I don't understand why I can't repartition or reformat it.

---

### Post by darkstaar on 2008-01-01
Bump

Does anybody know how I can recover the use of this 4GB USB flash drive?

Fdisk -l on this device outputs as follows:

> 

leisa@laptop:~$ fdisk -l /dev/sdb

Disk /dev/sdb: 4288 MB, 4288676352 bytes
132 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 8184 * 512 = 4190208 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       95081      234561   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(95080, 19, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(234560, 104, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       20613      257175   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(20612, 14, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(257174, 92, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      228481      465043   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(228480, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(465042, 95, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      352601      352608       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(352600, 44, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(352607, 15, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
leisa@laptop:~$ 




I'm not concerned about the data on the drive. I only wanted to recover the use of it. It's practically brand new.

---


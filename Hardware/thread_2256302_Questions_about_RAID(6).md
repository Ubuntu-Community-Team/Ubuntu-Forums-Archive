---
title: "Questions about RAID(6)"
date: 2014-12-11
forum: Hardware
---

### Post by PartisanEntity on 2014-12-11
I am in the process of setting up a home server. It's all up and running, now all that is left for me to do is set up a form of RAID for the file storage disks on the server.

I have 4 x 3TB disks.

Originally I wanted to go with RAID 5, but after much reading it appears that this level of raid is not recommended.

So I decided to go with RAID 6.

The problem is I cannot find any good tutorials explaining how this is done. I found many tutorials, but none seem consistent. Each suggests a different approach and I am unsure which is the best practice.

I set up a test machine to practice on (it's a virtual machine with 4 x 1GB virtual disks attached to it)

Here is what I did:

1. Format the 4 drives to ext 4.

2. Create a RAID 6 array using the following command:

```
mdadm ––create /dev/md0 ––level=6 ––raid-devices=4 /dev/sdc /dev/sdd /dev/sde /dev/sdd
```

3. I then made an ext file system on the raid device:

```
mkfs.ext4 /dev/md0
```

4. And lastly mounted this device at /mnt/raiddisk

Seems to be working. But I have no idea if I have missed some settings, or best practices that might give me a pain somewhere down the road.

Here is the output of cat /proc/mdstat:

> pe@ubuntutest:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdb1[0] sdc1[1] sde1[3] sdd1[2]
2091008 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

Here is the output of mdadm --detail /dev/md0:

> pe@ubuntutest: mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Dec 10 23:15:32 2014
     Raid Level : raid6
     Array Size : 2091008 (2042.34 MiB 2141.19 MB)
  Used Dev Size : 1045504 (1021.17 MiB 1070.60 MB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Thu Dec 11 14:42:28 2014
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntutest:0  (local to host ubuntutest)
           UUID : 0993d850:78d5a265:54ba94b5:c4c57c81
         Events : 17

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1


The output of fdisk -l:

> Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e620a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    37763071    18880512   83  Linux
/dev/sda2        37765118    41940991     2087937    5  Extended
/dev/sda5        37765120    41940991     2087936   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     2097151     1048575+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     2097151     1048575+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1     2097151     1048575+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1     2097151     1048575+  ee  GPT

Disk /dev/md0: 2141 MB, 2141192192 bytes
2 heads, 4 sectors/track, 522752 cylinders, total 4182016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Notice the output from fdisk -l, at the bottom it says: "Disk /dev/md0 doesn't contain a valid partition table". Is this something to worry about?

---

### Post by kpatz on 2014-12-11
The partition table message can be safely ignored since you didn't partition the array.

For 4 disks, RAID 5 is more efficient.  RAID 6 uses two of the drives for parity, so you're only going to get 2 TB of space from your 4 1 TB disks.  For 3-5 drives in an array use RAID 5, and for 6+ drives use RAID 6.  The advantage of RAID 6 is two drives can fail before you lose data.  But with 4 drives, the likelihood of having 2 fail within a short period is less.

If you want the redundancy of RAID 6 with just 4 drives, you'll get better performance with a RAID 1+0 (two mirrored pairs striped).

---

### Post by PartisanEntity on 2014-12-11
> **kpatz said:**
> If you want the redundancy of RAID 6 with just 4 drives, you'll get better performance with a RAID 1+0 (two mirrored pairs striped).

Thanks for that suggestion, RAID 1+0 does in fact appear to be the best option in comparison to my earlier decision of having wanted to create a RAID 6 array.

I just read up on the performance of RAID 5, 6 and 1+0. While raid 6 and 1+0 offer you 50% of your total capacity, RAID 1+0 has much better performance than 6.

I went ahead and created a RAID 1+0 array. It is syncing now.

---

### Post by PartisanEntity on 2014-12-11
Can I actually go ahead and mount the array while it is syncing? Or would it be better to wait until it has finished?

---

### Post by kpatz on 2014-12-11
You can mount it while it's syncing but it'll be slow to access until the sync is finished.

---

### Post by PartisanEntity on 2014-12-12
Now that it has finished syncing. I decided to run fdisk -l again just to see what the output is and I get the following:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00024b98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   226318335   113158144   83  Linux
/dev/sda2       226320382   234440703     4060161    5  Extended
/dev/sda5       226320384   234440703     4060160   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT
**Partition 1 does not start on physical sector boundary.**

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
**Partition 1 does not start on physical sector boundary.**

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  4294967295  2147483647+  ee  GPT
**Partition 1 does not start on physical sector boundary.**

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
**Partition 1 does not start on physical sector boundary.**

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 1500.3 GB, 1500299395072 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930272256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        2047        1023+  ee  GPT
/dev/sdg2            2048  2930270207  1465134080   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  3907024895  1953512447+  ee  GPT

Disk /dev/md0: 6000.9 GB, 6000913416192 bytes
2 heads, 4 sectors/track, 1465066752 cylinders, total 11720534016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

It seems the 4 drives that make up my raid all show the following message as bolded above: "Partition 1 does not start on physical sector boundary."

Is that an issue?

---

### Post by tgalati4 on 2014-12-14
You can get a little extra performance out of your disk drives by adding "padding" sectors so that the partition does end on a physical sector boundary.  How to do that and what performance gains you get depend on your specific hard drive model.  You would have to search for the best ways to do it and possible gains.

Because of the comlexity of RAID6 striping, the most gain in padding is probably from a single disk used in single-disk (non-RAID) mode.

---


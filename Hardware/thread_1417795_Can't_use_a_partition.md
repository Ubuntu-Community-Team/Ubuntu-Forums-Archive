---
title: "Can't use a partition"
date: 2010-02-27
forum: Hardware
---

### Post by jaredvv86 on 2010-02-27
I recently reinstalled and my old partition is now unable to be accessed.  When I go use the Disk Utility it shows up as unknown or unused used.  When I go into terminal it tells me the following info with the fdisk command

```
sudo fdisk -l
``````

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3a4a506

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1344    10791936   27  Unknown
/dev/sda2   *        1344       17011   125846409    7  HPFS/NTFS
/dev/sda3           17012       30401   107555175    5  Extended
/dev/sda5   *       26490       30234    30081712+  83  Linux
/dev/sda6           30235       30401     1341396   82  Linux swap / Solaris
/dev/sda7           17012       26096    72975199+  83  Linux
/dev/sda8           26097       26488     3148708+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders
Units = cylinders of 6550 * 512 = 3353600 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        2396     7839744    b  W95 FAT32


```sda5 is the old partition I am trying to get some files off of.  I am sort of new to Ubuntu so please go easy on me.  I have some files for a research paper on there that I would desperately like to get off.  Even getting a backup image of that partition to pull off would help.  Thanks

---

### Post by Ozymandias_117 on 2010-02-27
Have you tried manually mounting it to a folder? Make a folder (on your desktop is fine, I'll assume you've made a folder on your desktop named "test" for the command) You would then type "sudo mount -t ext4 /dev/sda5 /home/*username*/test" I assume the partition is ext4... if it's 3 just change it to ext3 ;)

---

### Post by jaredvv86 on 2010-02-27
Ozymandias thanks for your response.  When I tried your suggestion here is what I got.

```

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

looking in disk utility it seems that there is no filesystem attached to the partition.  Any other ideas?

---


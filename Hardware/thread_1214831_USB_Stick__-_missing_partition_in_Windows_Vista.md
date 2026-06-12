---
title: "USB Stick  - missing partition in Windows Vista"
date: 2009-07-16
forum: Hardware
---

### Post by ncmncm on 2009-07-16
Hello 

I think the answer to this might be simple. 

I have a 4GB USB stick. For learning purposes, I deleted the 4 partitions on it and used fdisk to create 2 2GB  partitons. Not knowing the  right code for FAT32, I used Gparted on the two partitions to made them FAT32.

In Ubuntu, the stick appears as it should:


```

cm@cm-laptop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 4215 MB, 4215799808 bytes
130 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 8060 * 512 = 4126720 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         510     2055269    b  W95 FAT32
/dev/sdb2             511        1021     2059330    b  W95 FAT32
```


However, when I inserted the USB stick on a Vista PC, it sees only one drive F: 

Can someone tell me what exactly is happening?

---

### Post by az on 2009-07-16
> **ncmncm said:**
> Hello 

I think the answer to this might be simple. 

I have a 4GB USB stick. For learning purposes, I deleted the 4 partitions on it and used fdisk to create 2 2GB  partitons. Not knowing the  right code for FAT32, I used Gparted on the two partitions to made them FAT32.

In Ubuntu, the stick appears as it should:


```

cm@cm-laptop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 4215 MB, 4215799808 bytes
130 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 8060 * 512 = 4126720 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         510     2055269    b  W95 FAT32
/dev/sdb2             511        1021     2059330    b  W95 FAT32
```


However, when I inserted the USB stick on a Vista PC, it sees only one drive F: 

Can someone tell me what exactly is happening?

You are looking at the partitions on the drive in Ubuntu.  You have not created any filesystem on it yet.  If you create filesystems on both the partitions, Windows should then see them and mount them automatically.  

I've noticed that if I create more than one partition on a USB drive and format the first partition to ext3 (or another filesystem that windows won't read) it ignores the whole drive.  But If all the filesystems are windows-friendly, it can access all of them just fine.

Also, setting the partition type is not the same as creating a fileysstem (formating).  To format them, run

(I assume the device is sdc)  (Use the correct device!)
mkdosfs -n USBdrive1 /dev/sdc1
mkdosfs -n USBdrive2 /dev/sdc2

---

### Post by irv on 2009-07-16
> **ncmncm said:**
> Hello 

I think the answer to this might be simple. 

I have a 4GB USB stick. For learning purposes, I deleted the 4 partitions on it and used fdisk to create 2 2GB  partitons. Not knowing the  right code for FAT32, I used Gparted on the two partitions to made them FAT32.

In Ubuntu, the stick appears as it should:


```

cm@cm-laptop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 4215 MB, 4215799808 bytes
130 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 8060 * 512 = 4126720 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         510     2055269    b  W95 FAT32
/dev/sdb2             511        1021     2059330    b  W95 FAT32
```


However, when I inserted the USB stick on a Vista PC, it sees only one drive F: 

Can someone tell me what exactly is happening?

This is probably another one of those Vista thing. When you read the "F" drive in Vista what is the size? Maybe Vista is reading the File Allocation table wrong. You might want to the control panel and admin>manages computer>disk drives and see if it is coming up greyed out. You might have to assign a drive letter manual.

---

### Post by ncmncm on 2009-07-18
> **irv said:**
> This is probably another one of those Vista thing. When you read the "F" drive in Vista what is the size? Maybe Vista is reading the File Allocation table wrong. You might want to the control panel and admin>manages computer>disk drives and see if it is coming up greyed out. You might have to assign a drive letter manual.


I created the filesystem like so:

> sudo mkvs.vfat -F 32 -n SDB1 /dev/sdb1
sudo mkvs.vfat -F 32 -n SDB2 /dev/sdb2


Irv, having checked the disk drives under Vista it  reports that  the total capacity is 4GB but only the first parition (called SDB1) is visible with capacity 2GB.

---

### Post by ncmncm on 2009-07-18
> **az said:**
> You are looking at the partitions on the drive in Ubuntu.  You have not created any filesystem on it yet.  If you create filesystems on both the partitions, Windows should then see them and mount them automatically.  

I've noticed that if I create more than one partition on a USB drive and format the first partition to ext3 (or another filesystem that windows won't read) it ignores the whole drive.  But If all the filesystems are windows-friendly, it can access all of them just fine.

Also, setting the partition type is not the same as creating a fileysstem (formating).  To format them, run

(I assume the device is sdc)  (Use the correct device!)
mkdosfs -n USBdrive1 /dev/sdc1
mkdosfs -n USBdrive2 /dev/sdc2

az, please see my previous post. I did create the  filesystem as outlined above.

Having exhausted all my options with **mkvs.vfat ** I think this suggestion with **mkdosfs **is something that I will try now. Will report my findings.

---

### Post by irv on 2009-07-18
> **ncmncm said:**
> Irv, having checked the disk drives under Vista it  reports that  the total capacity is 4GB but only the first parition (called SDB1) is visible with capacity 2GB.

Did you try what "az" posted above? 

```
mkdosfs -n USBdrive1 /dev/sdb1
mkdosfs -n USBdrive2 /dev/sdb2
```

---

### Post by ncmncm on 2009-07-18
> **irv said:**
> Did you try what "az" posted above? 

```
mkdosfs -n USBdrive1 /dev/sdb1
mkdosfs -n USBdrive2 /dev/sdb2
```

Irv, I  did not realise that mkfs.vfat and mkdosfs are the same. I did what Az said in the first place , except that I used an alias: **mkfs.vfat** instead of **mkdosfs.**  

To sum it up once again, I removed the original four partitions, created 2 2GB w95/ FAT32 partitions and  ran mkfs.vfat on both the partitions.

Still no luck with a Vista which conveniently condemned 2GB to nowhere.

---

### Post by irv on 2009-07-18
> **ncmncm said:**
> Irv, I  did not realise that mkfs.vfat and mkdosfs are the same. I did what Az said in the first place , except that I used an alias: **mkfs.vfat** instead of **mkdosfs.**  

To sum it up once again, I removed the original four partitions, created 2 2GB w95/ FAT32 partitions and  ran mkfs.vfat on both the partitions.

Still no luck with a Vista which conveniently condemned 2GB to nowhere.

I think it was around February  I had the same problem with Vista. I can't remember but I think I used my son's computer which was running XP to partition and format a USB Drive and it then read alright in Vista. I am not sure but I think there is something different about Vista. The first time I tried to partition and format it was in Ubuntu. I don't think the problem is Ubuntu, I think the problem is Vista. If you have a XP box somewhere maybe you should see if the stick reads right on that.
I know I was scratching my head on that one also.

---

### Post by ncmncm on 2009-07-18
I do have a XP system. Will try to check the USB stick on it. 

One nagging question though: What would you recommend as a file system for cross-compatibility?

---

### Post by irv on 2009-07-18
> **ncmncm said:**
> I do have a XP system. Will try to check the USB stick on it. 

One nagging question though: What would you recommend as a file system for cross-compatibility?

I always used F32 on all my USB drives. But I bought a 1TB USB Hard Drive and it came NTFS formated and I just left it, and I can read and write to it from Ubuntu 9.04. I use it for all my backups. I also partitioned a 2 GB partition on my laptop to copy file over to Windows. It reads it just fine and I formated it with fat32. I only mount it in Ubuntu when I need it. I also setup a Ubuntu One on the Internet to transfer file so no matter where I am I can get at these files.

---

### Post by az on 2009-07-18
Do the partitions mount automatically when you plug in the drive while running Ubuntu?

You've created the partitions correctly, using a proper ID for the partition - Windows has no reason to ignore them.  If they mount automatically in Ubuntu, then your formatted them correctly.

If it works in Ubuntu but not in Windows, I would conclude that this is a windows bug.

---


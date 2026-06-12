---
title: "accidentally changed my USB pen drive's file format to FAT32"
date: 2009-02-25
forum: Hardware
---

### Post by nightshade209 on 2009-02-25
i accidentally changed my USB pen drive's file format to FAT32, now ubuntu says it cannot mount the device as the file format is not supported. Pls tell me how to change it back, and most importantly what to change it back to. I think it was something like vfat or something before...

---

### Post by caljohnsmith on 2009-02-25
So did you actually format the partition on the USB drive as FAT32, or how did you "change the format"? How about posting:
```
sudo fdisk -lu
sudo parted -l
sudo blkid -c /dev/null
```

---

### Post by stchman on 2009-02-25
> **nightshade209 said:**
> i accidentally changed my USB pen drive's file format to FAT32, now ubuntu says it cannot mount the device as the file format is not supported. Pls tell me how to change it back, and most importantly what to change it back to. I think it was something like vfat or something before...

Ubuntu supports FAT, FAT32, NTFS, EXT2/3 OOB.  So that is not the problem.

All my USB flash drives are FAT32.

---

### Post by sr20ve on 2009-02-25
Vfat = fat32

---

### Post by nightshade209 on 2009-02-26
i did not reformat it, i just typed in FAT32 in the file system box in Volume in Properties of the pen drive...
here's the output to sudo fdisk -lu
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfe0dfe0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306600524   153300231   83  Linux
/dev/sda2       306600525   312576704     2988090    5  Extended
/dev/sda5       306600588   312576704     2988058+  82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, 4043309056 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  1936028272  3787887330   925929529+  68  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(116, 100, 32) logical=(249810, 12, 29)
Partition 1 has different physical/logical endings:
     phys=(288, 101, 46) logical=(488759, 81, 59)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?  1330184192  1869160479   269488144   79  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(357, 32, 43) logical=(171636, 83, 47)
Partition 2 has different physical/logical endings:
     phys=(0, 13, 10) logical=(241181, 124, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?   538989391  1937352302   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(69547, 2, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(249980, 117, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?  1394627663  1394648999       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(179951, 119, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(179954, 88, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

here's the output to sudo parted -l

```
 Model: ATA ST3160215AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  157GB  157GB   primary   ext3         boot 
 2      157GB   160GB  3060MB  extended                    
 5      157GB   160GB  3060MB  logical   linux-swap        


Model:   (scsi)
Disk /dev/sdb: 4043MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4043MB  4043MB  fat32     
```

and to sudo blkid -c /dev/null

```
 /dev/sda1: UUID="e59eb16e-0384-4f12-9514-99a8c9eadb44" TYPE="ext3" 
/dev/sda5: UUID="0eb81804-260f-4315-a34e-a091897cbe88" TYPE="swap" 
/dev/sdb: UUID="159F-2BA8" TYPE="vfat" 
```

---

### Post by nightshade209 on 2009-02-26
this is what i get everytime i put in my pen drive:

---

### Post by caljohnsmith on 2009-02-26
OK, how about trying:
```
sudo sfdisk -c /dev/sdb 1 c
```
If that command completes successfully, please post the output of:
```
sudo fdisk -lu
sudo vol_id --probe-all /dev/sdb1
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```
Also, what version of Ubuntu are you running?

---

### Post by stchman on 2009-02-26
> **nightshade209 said:**
> this is what i get everytime i put in my pen drive:

Use gparted to reformat the drive.

---

### Post by nightshade209 on 2009-02-28
> **caljohnsmith said:**
> OK, how about trying:
```
sudo sfdisk -c /dev/sdb 1 c
```
If that command completes successfully, please post the output of:
```
sudo fdisk -lu
sudo vol_id --probe-all /dev/sdb1
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```
Also, what version of Ubuntu are you running?

I am using 8.10, Intrepid.
After i ran this : ```
sudo sfdisk -c /dev/sdb 1 c
``` it just said "DONE".
Here are the outputs:

sudo fdisk -lu
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfe0dfe0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306600524   153300231   83  Linux
/dev/sda2       306600525   312576704     2988090    5  Extended
/dev/sda5       306600588   312576704     2988058+  82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, 4043309056 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  1936028272  3787887330   925929529+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(116, 100, 32) logical=(249810, 12, 29)
Partition 1 has different physical/logical endings:
     phys=(288, 101, 46) logical=(488759, 81, 59)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?  1330184192  1869160479   269488144   79  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(357, 32, 43) logical=(171636, 83, 47)
Partition 2 has different physical/logical endings:
     phys=(0, 13, 10) logical=(241181, 124, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?   538989391  1937352302   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(69547, 2, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(249980, 117, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?  1394627663  1394648999       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(179951, 119, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(179954, 88, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

sudo vol_id --probe-all /dev/sdb1
```
/dev/sdb1: error opening volume

```

sudo mount /dev/sdb1 /mnt && ls -l /mnt
```
mount: special device /dev/sdb1 does not exist
```

---

### Post by nightshade209 on 2009-02-28
> **stchman said:**
> Use gparted to reformat the drive.

Could you pls tell how? I am not familiar with gparted...

---

### Post by kelvin spratt on 2009-02-28
If this is any help this is what I get as you can see your entry is not correct as the label is wrong, try another pen drive to see if its only that 1 giving you problems.
[ sudo blkid -c /dev/null
/dev/sda1: UUID="2648AE8B48AE5977" TYPE="ntfs" 
/dev/sda5: UUID="84a9411d-3edc-42b7-8e1d-aff28d941d40" TYPE="swap" 
/dev/sda6: UUID="5dc45e5a-849b-4a13-b101-991c5411e85f" TYPE="jfs" 
/dev/sda7: UUID="00c2541b-a149-4f64-bb2c-b52392fb0721" TYPE="jfs" 
/dev/sda8: UUID="d8e6f758-9024-4883-ad18-d8af1f5bf798" TYPE="jfs" 
/dev/sda9: UUID="2a705f5e-7b6f-47d1-bbfd-96d47aa85588" TYPE="jfs" 
/dev/sdb1: UUID="5e258e37-b172-4941-9f52-44591c5b711e" TYPE="jfs" 
/dev/sdb5: UUID="fc86cc09-386b-44a9-8676-e9dfec22e7c8" TYPE="jfs" 
/dev/sdb6: UUID="2e71f9b8-839f-483c-8d1a-baaaa15db967" TYPE="jfs" 
/dev/sdb7: UUID="506bdaf9-b747-4f2c-8765-23e476e25316" TYPE="jfs" 
/dev/sdb8: UUID="4857-BE18" TYPE="vfat" 
/dev/sdc1: UUID="22F0455AF0453577" TYPE="ntfs" 
/dev/sdc2: UUID="78E0445DE04423AA" TYPE="ntfs" 
/dev/sdc3: UUID="C81023C71023BAF8" TYPE="ntfs" 
/dev/sdc4: UUID="86C42C24C42C1947" TYPE="ntfs" 
/dev/sdd1: LABEL="USB DISK" UUID="C85D-FDB2" TYPE="vfat"

---

### Post by caljohnsmith on 2009-02-28
If you want to use gparted to reformat your USB drive, you can either use gparted from the Live CD under (System > Admin > Partition Editor), or you can install gparted into your Ubuntu with:
```
sudo apt-get install gparted
```
When you run gparted, just make sure to select your USB drive in the drop-down list of drives that it provides. Then if you go to Device > Create New Partition Table (use the default MS-DOS partition table), that will allow you to start fresh on that drive and create new partitions.

---

### Post by nightshade209 on 2009-03-01
> **caljohnsmith said:**
> If you want to use gparted to reformat your USB drive, you can either use gparted from the Live CD under (System > Admin > Partition Editor), or you can install gparted into your Ubuntu with:
```
sudo apt-get install gparted
```
When you run gparted, just make sure to select your USB drive in the drop-down list of drives that it provides. Then if you go to Device > Create New Partition Table (use the default MS-DOS partition table), that will allow you to start fresh on that drive and create new partitions.

i created a MS-DOS partition table, now it just shows unallocated filesystem. Which filesystem shud i use? It gives ext2, ext3, fat16, fat32,linux-swap, reiserfs and unformatted as options. I need to use it on Linux, Windows and OpenSolaris systems...

---

### Post by vanadium on 2009-03-01
For what you want, I recommend fat32. It is most compatible.

---

### Post by nightshade209 on 2009-03-04
thanx everyone! problem solved! :D

---


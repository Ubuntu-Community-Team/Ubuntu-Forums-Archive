---
title: "Cannot mount Western Digital 2.0 USB 2TB on Ubuntu Lucid"
date: 2010-10-22
forum: Hardware
---

### Post by shayno90 on 2010-10-22
Error mounting: mount exited with exit code 12: Failed to read last sector (3907027119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

How can I mount this external HDD onto the system?

---

### Post by coffeecat on 2010-10-22
> **shayno90 said:**
> How can I mount this external HDD onto the system?

The error message is telling you something is probably seriously wrong with the filesystem, so you're not going to be able to mount it without some investigation.

Is this a brand-new drive that you are trying to use for the first time? Or is it one with data you are trying to access? If the latter, did you unmount it cleanly the last time you used it? If you have used it before, which operating system were you using? Do you have access to Windows? If so, what happens when you plug it in to Windows?

If it's not brand-new, has it been reformatted by yourself and, if so, how did you format it?

When you tried to mount it this time, what was the exact mount command you used?

Lastly, which is the exact model of the WD drive? Is it a bare drive that you've put in an enclosure or did it come as a complete WD unit, enclosure and all? There are some WD's which come with some sort of bizarre Windows backup software on a sort-of hidden partition come flash drive. They have been causing big problems with both Linux and MacOS.

---

### Post by shayno90 on 2010-10-22
> **coffeecat said:**
> The error message is telling you something is probably seriously wrong with the filesystem, so you're not going to be able to mount it without some investigation.

Is this a brand-new drive that you are trying to use for the first time? Or is it one with data you are trying to access? If the latter, did you unmount it cleanly the last time you used it? If you have used it before, which operating system were you using? Do you have access to Windows? If so, what happens when you plug it in to Windows?

If it's not brand-new, has it been reformatted by yourself and, if so, how did you format it?

When you tried to mount it this time, what was the exact mount command you used?

Lastly, which is the exact model of the WD drive? Is it a bare drive that you've put in an enclosure or did it come as a complete WD unit, enclosure and all? There are some WD's which come with some sort of bizarre Windows backup software on a sort-of hidden partition come flash drive. They have been causing big problems with both Linux and MacOS.

Yep it's a brand new drive, 3.5 inch external hard drive
**[SIZE=2][WESTERN DIGITAL]("http://www.pixmania.ie/ie/uk/western-digital/3177/marque.html") 	                                           WD Elements Desktop 2 TB USB 2.0 External Hard Drive - black                 [/SIZE]**

No data on the drive as it is new.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=bf00db6b-11e7-442c-b27b-7e508a37c0cc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=63fc54eb-ccbe-43ae-aabe-7785981c2d56 none            swap    sw              0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50d0ccd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       20978   168300544    7  HPFS/NTFS
/dev/sda3           20979       37286   130985985    5  Extended
/dev/sda4           37286       38914    13077504    7  HPFS/NTFS
/dev/sda5           20979       36618   125622272   83  Linux
/dev/sda6           36618       37286     5362688   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002de0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953513560    7  HPFS/NTFS

---

### Post by coffeecat on 2010-10-22
> **shayno90 said:**
> **WD Elements**

That's good. It's the My Passport Elite drives that seem to be causing problems.

Coincidentally, I bought myself a WD Elements 1TB drive (NTFS) the other day and that seems to be behaving perfectly.

fdisk seems happy with the drive, but that only reads the partition table entries anyway. If that were my drive, I'd be tempted to reformat it and be done with it. If you do, and you use Gparted, make sure you use the version in 10.04 or 10.10 - nothing earlier - although I see you are using 10.04 anyway. That WD drive will be one of the new 'advanced format' drives and you need the later version of Gparted to get the first sector in the correct place. Or use Vista or Windows 7, not XP, if you want to format it NTFS again.

---

### Post by colin.p on 2010-10-22
WD has done something in the way they format drives. Windows will read them, but not linux. I have a WDTV Live which runs linux and on the WD forums, there are alot of people having a problem with the Live not reading brand new WD drives, some but not all. WD's solution is to re-format the drives, so the Live (linux) will read them. Maybe something to do with cluster size?

---

### Post by shayno90 on 2010-10-23
Can I not just install []("http://www.linuxforums.org/forum/#")NTFS as a partition in order for the external hard drive to mount on both Windows 7 and Ubuntu 10.04?
 
sudo apt-get_ install _
gparted ntfsprogs           Maybe?

---

### Post by coffeecat on 2010-10-23
I'm not sure what all that blue BBCode that's gone wrong means but, yes, install Gparted and reformat the drive. Yes, you'll need ntfsprogs as well but I think that came with 10.04. You can check that in Synaptic anyway.

Partitions formatted as NTFS in Gparted will mount quite happily in both Windows and Ubuntu. I've done that several times with external drives.

---

### Post by psusi on 2010-10-23
I spoke with someone on irc the other night with the same issue.  It seems that either WD is shipping the drive with a bad format, or the usb enclosure is broken and making the drive appear a bit smaller than it really is.  I could not find detailed specifications on exactly how many sectors the drive is supposed to have so I could not tell.

Windows will mount the drive, but if you run a chkdsk on it, will tell you that it is broken with a similar error.  Reformat and it should be fine.

---

### Post by shayno90 on 2010-10-25
:~$ sudo fdisk -l /dev/sda
[sudo] password: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50d0ccd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       20978   168300544    7  HPFS/NTFS
/dev/sda3           20979       37286   130985985    5  Extended
/dev/sda4           37286       38914    13077504    7  HPFS/NTFS
/dev/sda5           20979       36618   125622272   83  Linux
/dev/sda6           36618       37286     5362688   82  Linux swap / Solaris

Ok, I will reformat it using the disk manager on WIndows 7?

---

### Post by coffeecat on 2010-10-25
> **shayno90 said:**
> :~$ sudo fdisk -l /dev/sda

....

Ok, I will reformat it using the disk manager on WIndows 7?

Why are you...

```
sudo fdisk -l /dev/sda
```?

That will only output your internal drive. Is that why you are thinking of using Windows to reformat it? No need. If you want to check **all** your partitions...

```
sudo fdisk -l
```Or easier to read:

```
sudo fdisk -lu
```And, anyway, why bother with fdisk? Just open up Gparted and reformat the external drive.

---

### Post by shayno90 on 2010-10-28
Ok, tried reformatting using Windows volume manager and it failed and now the drive is "raw" with no system on it and trying to mount now doesn't work in Ubuntu! What next?

~$ sudo fdisk -l
[sudo] password : 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50d0ccd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       20978   168300544    7  HPFS/NTFS
/dev/sda3           20979       37286   130985985    5  Extended
/dev/sda4           37286       38914    13077504    7  HPFS/NTFS
/dev/sda5           20979       36618   125622272   83  Linux
/dev/sda6           36618       37286     5362688   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002de0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953513560    7  HPFS/NTFS

---

### Post by psusi on 2010-10-28
You need to delete the partition and recreate it since it extends past the end of the drive.

---

### Post by srs5694 on 2010-10-28
> **psusi said:**
> You need to delete the partition and recreate it since it extends past the end of the drive.

That might not be true. Disks rarely have a number of sectors that divides exactly into the cylinder size. Thus, there are usually some "leftover" sectors at the end of the disk. These sectors are usable, and it's legal to create a partition that includes them. The total number of cylinders reported by fdisk does not include those sectors, though, and when you create a partition that moves far enough into that area, the end cylinder number for that partition will rise above the number of cylinders on the disk. (I don't happen to know the exact rules that fdisk uses for rounding to cylinder numbers, though.) This sort of condition is rarely seen in old disks that were partitioned using cylinder disk boundaries, but it can be seen in disks that have been partitioned with newer software that ignores cylinder boundaries. It's very common in the MBR protective partitions on GPT disks. To be sure of what's going on, you need to use the -u option to fdisk, as in "sudo fdisk -lu".

Here's a demonstration, using a GPT disk:

```

$ sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488386583+  ee  GPT
$ sudo fdisk -lu /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

```

As you can see from the first output, the disk has 60801 cylinders and the GPT protective partition ends on cylinder 60802, according to fdisk; but changing the units to sectors shows that the disk has 976,773,168 sectors, and the GPT protective partition ends on sector 976,773,167 (the last sector on the disk). That MBR partition is perfectly legal, but it seems to end after the end of the disk, if you go by cylinder numbers.

I really wish they'd just do away with "cylinder" numbering, which hasn't been relevant for well over a decade. Continuing to use it today just causes confusion.

---

### Post by srs5694 on 2010-10-28
> **shayno90 said:**
> Ok, tried reformatting using Windows volume manager and it failed and now the drive is "raw" with no system on it and trying to mount now doesn't work in Ubuntu! What next?

Without knowing what sort of error Windows gave you, it's hard to know what the cause was. Try this in Linux, and if it fails, post the exact error message:

```

sudo mkfs.ntfs /dev/sdb1

```

*Be sure to get the device filename (/dev/sdb1) right!* If you accidentally get that wrong, you could destroy another partition. If you get a "command not found" error, you need to install the ntfsprogs package.

---

### Post by krige on 2010-10-29
I had the same problem, the disk was new, no data on it. I used GParted to create a new partition table and then a new NTFS partition. The drive seems to work fine now, I didn't need to format it.

---

### Post by psusi on 2010-10-29
srs, fdisk rounds the cylinder count the same way for the partition size and the disk size.  As a result, if the end cyl of the partition is the same as the disk, you can not tell for sure if it actually fits, but if the partition cyl is > than disk cyl count, then it definitely extends beyond the end of the disk, just like other users of this same drive.  I do not know why but WD ships them formatted wrong.

---

### Post by srs5694 on 2010-10-29
> **psusi said:**
> srs, fdisk rounds the cylinder count the same way for the partition size and the disk size.  As a result, if the end cyl of the partition is the same as the disk, you can not tell for sure if it actually fits, but if the partition cyl is > than disk cyl count, then it definitely extends beyond the end of the disk, just like other users of this same drive.  I do not know why but WD ships them formatted wrong.

Please re-read my post, and particularly the demonstration in the code block. It proves you're wrong about the cylinder/partition issue. Of course, it could be that shayno90's partition is too big for the disk, but it will take the output of "sudo fdisk -lu /dev/sdb" to be sure.

---

### Post by psusi on 2010-10-29
Oh weird, it is rounding down when reporting the size of the disk.  How goofy.

---

### Post by srs5694 on 2010-10-29
> **psusi said:**
> Oh weird, it is rounding down when reporting the size of the disk.  How goofy.

It makes perfect sense, actually. When you're entering sizes in terms of cylinders, you can't use a partial cylinder. For instance, suppose a disk has a number of sectors that works out to 1000.3 cylinders. If the utility reported the size as, and permitted entry of cylinder values up to, 1001, then a partition that ended on cylinder 1001 would be too big for the disk. Thus, the utility reports the number of cylinders as 1000 and accepts values only up to that size. When you switch out of cylinder mode and enter an end value in sectors that's as large as is possible, though, fdisk appears to round that value up, which causes confusion. It might be less confusing if fdisk rounded down in such situations, but I haven't thought through all the possible consequences of that -- perhaps some other situation would end up being confusing in that case.

Hence, my growing annoyance with the whole cylinder numbering scheme. It wasn't really that bad when most disks were partitioned to begin and end on cylinder boundaries, but now that many utilities are abandoning it, the fact that fdisk is still using it as its default is just causing problems.

---

### Post by shayno90 on 2010-10-31
> **srs5694 said:**
> Without knowing what sort of error Windows gave you, it's hard to know what the cause was. Try this in Linux, and if it fails, post the exact error message:

```

sudo mkfs.ntfs /dev/sdb1

```*Be sure to get the device filename (/dev/sdb1) right!* If you accidentally get that wrong, you could destroy another partition. If you get a "command not found" error, you need to install the ntfsprogs package.

:~$ sudo mkfs.ntfs /dev/sdb1
[sudo] password for shayno90: 
The device doesn't exist; did you specify it correctly?

~$ sudo fdisk -l /dev/sdd

Disk /dev/sdd: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005737f

   Device Boot      Start         End      Blocks   Id  System

~$ sudo dd if=/dev/zero of=/dev/sdb

Executed the above command and the device is not being recognised and cannot be edited on Gparted only can add a partition to it. Can I make an NTFS partition on it?

---

### Post by oldfred on 2010-10-31
Your sdb drive has become sdd? Just to add to the confusion.

---

### Post by shayno90 on 2010-10-31
> **oldfred said:**
> Your sdb drive has become sdd? Just to add to the confusion.


 	Code:
 	sudo dd if=/dev/zero of=/dev/sdb 
This will zero out the entire disk from start to finish; only then  can you create a partition table on the drive and create a primary Ext4  partition on the drive.

However it takes too long to format and changed the name to sdd instead of sdb.

$ dmesg | tail
[26087.596773] ath9k: Unable to stop TxDMA. Reset HAL!
[28049.717493] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
[28682.746005] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
[31540.950053] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
[31666.072577] CE: hpet increasing min_delta_ns to 33750 nsec
[33212.824077] usb 5-1: USB disconnect, address 3
[33212.824744] uhci_hcd 0000:00:1d.0: dma_pool_free buffer-2048, f238a800/3238a800 (bad dma)
[34766.216673] ath9k: Failed to stop TX DMA in 100 msec after killing last frame
[34766.225342] ath9k: Failed to stop TX DMA in 100 msec after killing last frame
[34766.225367] ath9k: Unable to stop TxDMA. Reset HAL!

---

### Post by shayno90 on 2010-10-31
~$ sudo fdisk -l /dev/sdb
[sudo] password for shayno90: 

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005737f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001    7  HPFS/NTFS

The device is working now after I used the Gparted to add the NTFS partition.

---

### Post by coffeecat on 2010-10-31
> **shayno90 said:**
> Code:
     sudo dd if=/dev/zero of=/dev/sdb 
This will zero out the entire disk from start to finish; only then  can you create a partition table on the drive and create a primary Ext4  partition on the drive.

Eh? Where did you get that from? You don't have to zero out a drive before you can recreate a partition table. And if you really want to zero out a partition table, you only need to zero the first 512 bytes of the drive - for an mbr partition table, that is.

'sudo dd if=/dev/zero of=/dev/sdb' will certainly zero out the whole drive. It will also waste some hours of your life.

---


---
title: "Data recovery from NTFS partition"
date: 2008-07-26
forum: General Help
---

### Post by librarian on 2008-07-26
I have been trying to recover data from a failing WinXP Dell laptop hard drive. I would like to recover everything just as it was, but barring that I need to recover several Audacity project (.aup) files. The drive fails the Dell diagnostic hard drive tests during read tests.

I have hooked up the dying drive to my Ubuntu 8.04 desktop via a SATA->USB adapter kit. I believe I was able to successfully image 1) the drive as a whole and 2) the target NTFS partition in separte runs using ddrescue as per the instructions at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) . But I don't know where to go from here. Whether I do the mmls math on 1) and try to mount the NTFS partition, or simply try to mount 2), I get something like 

```
NTFS signature is missing. 
Failed to mount '[DRIVE IMAGE FILE]' : Invalid argument
The device '[DRIVE IMAGE FILE]' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

What should my next step be?

---

### Post by logos34 on 2008-07-26
> **librarian said:**
> I believe I was able to successfully image 1) the drive as a whole and 2) the target NTFS partition in separte runs using ddrescue as per the instructions at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) . But I don't know where to go from here. Whether I do the mmls math on 1) and try to mount the NTFS partition, or simply try to mount 2), 

So, you can't mount the partition on the destination drive, where you dd'd the image?

---

### Post by librarian on 2008-07-26
> **logos34 said:**
> So, you can't mount the partition on the destination drive, where you dd'd the image?

here's what I tried last, and the resulting error is posted above:

```
sudo mount -t ntfs /lozier/SUNDANCE-p2.dd mnt/SUNDANCE
```

sundance was the name of the laptop...

---

### Post by logos34 on 2008-07-26
> **librarian said:**
> hsudo mount -t ntfs /lozier/SUNDANCE-p2.dd mnt/SUNDANCE

I believe you want [COLOR=Blue]**/**[/COLOR]mnt/SUNDANCE (unless you have a dir 'mnt' in home)

But you might want to post your 

sudo fdisk -l

identify the partitions (where the image is)

---

### Post by librarian on 2008-07-26
Oops!

Anyhoo, 

```
sudo mount -t ntfs /lozier/SUNDANCE-p2.dd /mnt/SUNDANCE
```

yields the same results...

```

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009e533

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58336   468583888+  83  Linux
/dev/sda2           58337       60801    19800112+   5  Extended
/dev/sda5           58337       60801    19800081   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x535f5849

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10443    83883366    7  HPFS/NTFS

```

The rescued image is on sda1 - sdb is blank excepting the 80G partition.

---

### Post by logos34 on 2008-07-26
i'd try either restoring the image to a new partition or else use something like PhotoRec--maybe it can recover those audacity files (it does other file formats besides .jpeg, etc, but not sure if that extends to audio-type files)

Create a new primary partition in sdb (same size as the original ntfs partition you recovered), and restore the image there---see if you can mount it that way
[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)
(--> restore image)

---

### Post by librarian on 2008-07-26
I'm afraid Photorec can't recover the aup files (or at least they aren't on the canonical list...)

Thanks for the advice on the new partition. I'll give it a shot right now...

---

### Post by librarian on 2008-07-27
I restored the image to a new 80G partition on my secondary hard drive

```
% sudo ddrescue /lozier/SUNDANCE-p2.dd /dev/sdb1 /lozier/SUNDANCE-p2-mv2sdb1.log

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:    79933 MB,  errsize:       0 B,  current rate:   80871 kB/s
   ipos:    79933 MB,   errors:       0,    average rate:   74341 kB/s
   opos:    79933 MB

```

And everything seems good... but when I try to mount, it won't.

```
% sudo mount -t ntfs /dev/sdb1 /mnt/SUNDANCE/

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

Any advice?

---

### Post by librarian on 2008-07-29
When I try to mount an image from an undamaged drive, I get the same errors. Hrm...

---

### Post by librarian on 2008-08-02
> **librarian said:**
> When I try to mount an image from an undamaged drive, I get the same errors. Hrm...

Heh - turns out the image from the good disk was FAT32, not NTFS. Mounting without the '-t ntfs' worked just fine on this image from a non-failing disk.

Anyhoo, when I ran 
```
sudo fsck -y
```
against the image from the partition from the good disk, it announced 
```
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/lozier/image-from-new-Dell.dd: 13418 files, 712707/8177174 clusters
```
but when I ran fsck -y against the image from the partition from the bad drive it doesn't think it's looking at an NTFS partition
```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /lozier/SUNDANCE-p2.dd

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---


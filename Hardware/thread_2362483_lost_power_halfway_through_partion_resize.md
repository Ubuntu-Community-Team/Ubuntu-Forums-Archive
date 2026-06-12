---
title: "lost power halfway through partion resize"
date: 2017-05-29
forum: Hardware
---

### Post by ktat on 2017-05-29
Hi,

I was using gparted to resize a partion on my backup drive when the battery went flat on my laptop, oops.  I can still mount the drive and the filesystem seems intact, however, when I tried to complete the process with gparted it gets stuck "searching /dev/sdb partitions"

I tried:
```
sudo fsck -y /dev/sdb
```

and got the following output:
```
fsck from util-linux 2.28.2
e2fsck 1.43.3 (04-Sep-2016)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a dos partition table in /dev/sdb
```

I then tried the e2fsck options with the different block numbers with no luck.

I would like to shrink the partition so that I can put a back up of my new windows system on there (just in case I screw it up when I try to dual boot lubuntu).

ta

---

### Post by ajgreeny on 2017-05-29
Using gparted try creating a new partition table from the Device menu.

It will, of course, mean any data on the current partition(s) is lost, but I suspect that would be so in any case, having stopped the procedure part way through while resizing.

If a new partition table does not help you I do not know what else to suggest, but others may have ideas, so don't totally give up just yet.

---

### Post by yancek on 2017-05-29
Does fdisk show any partitions/filesystems on sdb?  You're running a filesystem check on the entire device and that is usually done on the filesystem of a specific partition, i.e., sdb1.
If fdisk shows partitions, run the fsck commands suggested on them.

---

### Post by ktat on 2017-05-30
> **yancek said:**
> Does fdisk show any partitions/filesystems on sdb?  You're running a filesystem check on the entire device and that is usually done on the filesystem of a specific partition, i.e., sdb1.
If fdisk shows partitions, run the fsck commands suggested on them.

Thanks Yancek,  this is the output from fdisk:

```
Command (m for help): p
Disk /dev/sdb: 931.5 GiB, 1000170586112 bytes, 1953458176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00023f15

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953458175 1953456128 931.5G  7 HPFS/NTFS/exFAT

Command (m for help): i
Selected partition 1
         Device: /dev/sdb1
          Start: 2048
            End: 1953458175
        Sectors: 1953456128
      Cylinders: 121598
           Size: 931.5G
             Id: 7
           Type: HPFS/NTFS/exFAT
    Start-C/H/S: 0/32/33
      End-C/H/S: 1023/254/63


```

So the partition is seen, however, it doesn't seem to be an ext filesystem.  Any ideas where to from here?

---

### Post by yancek on 2017-05-30
> sudo fsck -y /dev/sdb

The above from your first post will never work in this situation because the 'fsck' command only does repairs on Linux filesystems and the filesystem on your device partition (sdb1) is a proprietary microsfot windows filesystem.  You need to run chkdsk /f on the partition which you should be able to do from your windows installation DVD/usb.  If you don't have one, you might be able to download something to burn to a CD and use, might be able to use a windows recovery disk although I'm not sure about that.

---

### Post by efflandt on 2017-05-31
It is best to use Windows' own "Disk Management" to resize NTFS partitions (or chkdsk /f from Windows to fix them).

---

### Post by ktat on 2017-06-03
The chkdsk /f command worked a treat, thank you.

I did find, though, that I was unable to shrink the partition to the size I wanted with the windows disk manager application.  I tried a number of different sizes and kept getting the error message that the disk doesn't have enough space to complete the task.

So, I tried with gparted again (this time with the power connected).  Process hasn't completed, but seems to be going well.*

*famous last words????

---

### Post by yancek on 2017-06-03
Windows usually won't shrink a partition to less than half it's original size from what I have read.  Gparted should.  If you use GParted, boot windows and do chkdsk /f again.

---

### Post by oldfred on 2017-06-03
Windows NTFS really likes lots of room or 30% free space inside it.
If you get down to 10% free it slows down and a defrag can take forever.
So do not make too small or houseclean.

While discussing Vista, it still applies to newer Windows.
 [http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---


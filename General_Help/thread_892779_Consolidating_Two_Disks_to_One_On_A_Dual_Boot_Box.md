---
title: "Consolidating Two Disks to One On A Dual Boot Box"
date: 2008-08-17
forum: General Help
---

### Post by Chernevik on 2008-08-17
I need some help figuring out the best way to consolidate files stored on two drives onto one, and then backup that one to the other using dd or rsync.

Here's the problem: I want to set up my two hard drives so I can recover from a failure on the first drive by swapping it out with the second, which should be able to boot the machine as if it were the first.  I think I can do this by keeping everything on the first drive and continuously copying it to the second with something like dd or rsync, but I screwed up the install have files spread over both drives.  

The computer dual boots Ubuntu 7.04 and Windows XP, and has two large hard drives.  Windows is installed on two partitions, one for OS and program files, the other for data.  The boot sector, Windows data and Linux files are on one drive, and the Windows OS and program files are on the second.  I have swap partitions on both drives, and the linux 'root' (not '/', '/root') directory is on the second.

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39373937

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9092    73031458+   7  HPFS/NTFS
/dev/sda2            9093       89972   649668600   83  Linux
/dev/sda3           89973       91201     9871942+   5  Extended
/dev/sda5           89973       91201     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x398e398e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       91200   630165690    f  W95 Ext'd (LBA)
/dev/sdb5           12749       25496   102398278+  83  Linux
/dev/sdb6           25497       31870    51199123+  82  Linux swap / Solaris
/dev/sdb7           31871       32890     8193118+   e  W95 FAT16 (LBA)
/dev/sdb8           32891       91200   468375043+   e  W95 FAT16 (LBA)

The Windows installation has the OS and program files in one partition, and the data files in a second.  

I looked at /proc/mounts to see which devices were mounted to which directories.  
- The / directory is the target of the mount /dev/disk/by-uuid/289..., which is itself a symlink to /sda2, so I guess the /sda2 partition holds the linux filesystem.
- /media/disk, which holds the Windows data files, is the target of the mount /sda1.  This is also the boot disk.
- /media/disk-1, which holds the Windows OS and program files, is the target of /sdb1.  

I also explored /dev/disk/by-uuid, which has these entries:
- /sda1, which holds the Windows data and is the boot sector (shown by /proc/mounts to be mounted as /media/disk)
- /sda2, as the target of a symbolic link from /dev/disk/by-uuid/289.... -- so I suppose my Linux filesystem is held on that partition of the sda drive.  
- /sda5, which also appears to be a swap volume
- /sdb1, which holds the Windows OS and program files (shown by /proc/mounts to be mounted as /media/disk-1)
- /sdb5, which which also appears in /dev/disk/by-label as the target of the symbolic link for 'root'
- /sdb6, which seems from fdisk to be a swap volume

I'm wondering if sdb2, sdb7 and sdb8 are somehow required by Windows.  They don't appear on the Ubuntu file browser.  The /sda3 partition is also unaccounted for, and I wonder what that's doing.

One approach:
- verify that the sdb5, sdb7 and sdb8 partitions don't hold anything important
- create a partition on sda to receive the contents of sdb1, taking space from sda2; and another for the contents of sdb5, again taking space from sda5
- leave sda3 alone, as I don't need the space
- copy the contents of sdb1 and sdb5 to these new partitions on sda1
- tell linux to look to these new partitions rather than sdb1 and sdb5
- tell linux to rely solely on sda5 for swap partition
- disconnect the sdb drive and verify that Unix and XP both boot, and that the files are present as before
- reformat sdb and then copy over the sda drive with dd or rsync.

But I've got several problems:
- Both sda5 and sdb6 are identified as Linux swap partitions:
  > Which one is the system using?
  > If sda5 is the swap, and I overwrite with my repartition effort, will that crash the system?  Should that repartition preserve sda5?
  > If sdb6 is the swap, how do I get Linux to use sda5?  Would the larger size of sdb6 matter?
- The Id #s 83 and 82 are duplicated.  Does that mean that the os thinks those volumes/partitions are somehow the same?
- Messing around with a directory named 'root' seems dangerous.
- Can I revise the partitions on sda without blowing up the boot partition?

And I've got several operational questions:
- How do I create the target partitions on sda?
- How do I copy the contents of the volumes/partitions on sdb to their newly created homes on sda?  cp doesn't seem to do it.
- Once I've copied the sdb partitions to sda, how do I tell linux and grub to refer to the sda partitions rather than the sdb partitions?

Thanks.

---

### Post by treehouse on 2008-08-24
Have you considered using a RAID setup?

---


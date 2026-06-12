---
title: "fuse: mount failed: Device or resource busy"
date: 2012-02-11
forum: Hardware
---

### Post by Dolgoth on 2012-02-11
Hi,

Sorry I have tried various threads but can't seem to find one that works for me.

I have got a ubuntu 11.10 server running recently which I set up with samba. I had the samba share working correctly and everything until I had a power cut - the server went down hard. The samab share was on an external but I can no longer get it to mount. I have tried various steps but I am a noob so think I am going in circles.

sudo mount -a
fuse: mount failed: Device or resource busy



sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047263

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/mapper/UBUNTUSERVER-root: 157.6 GB, 157642915840 bytes
255 heads, 63 sectors/track, 19165 cylinders, total 307896320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/UBUNTUSERVER-root doesn't contain a valid partition table

Disk /dev/mapper/UBUNTUSERVER-swap_1: 2139 MB, 2139095040 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4177920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/UBUNTUSERVER-swap_1 doesn't contain a valid partition table

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0025be3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953519615   976758784    7  HPFS/NTFS/exFAT

Disk /dev/mapper/1WD      Ext HDD 1021    WCAV5F597157    : 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0025be3d

                                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/1WD      Ext HDD 1021    WCAV5F597157    1            2048  1953519615   976758784    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
81 heads, 63 sectors/track, 45941 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a74d7aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   234441647   117219800   83  Linux

any help please....

---

### Post by josephmills on 2012-02-11
please try to un mount it first open terminal and type in ```
man umount 
``` there could be other thingsgoing on but.. for now that that

---

### Post by ahallubuntu on 2012-02-11
If the disk that you are having trouble with is an Linux ext3/ext4 partition, run e2fsck on it.

If the disk that you are having trouble with is a Windows partition (NTFS or FAT32), I suggest you run chkdsk on it in Windows to fix any possible file system issues caused by the power failure.

FYI, there is no need to use Windows filesystems like NTFS for a Samba server.  There are good reasons to use NTFS (I would avoid FAT32 at this point - one limitation is no files larger than about 4GB in that file system) if you will be interchanging the disk with Windows computers.  But Samba works fine with ext3/ext4.  Windows computers connecting to it still see it as a Windows share and don't know/care what format the actual disk is in.

---

### Post by Dolgoth on 2012-02-12
Thanks,

I seem to have got it working. I couldn't umount it but I ended up taking it to a Win 7 machine (2nd time) and tried: chkdsk /R

When I put it back in it seemed to work it did however pick up a ne name/id in dev. It is no longer sdb but now sde. Not sure why but I can mount it now which is the important bit.

Thanks for the info on the samba share - I didn't realize that. Although on this occasion the drive already had data on so would have kept it anyway but good knowledge for future shares. Is there any better performance for win clients when using different formats?

---


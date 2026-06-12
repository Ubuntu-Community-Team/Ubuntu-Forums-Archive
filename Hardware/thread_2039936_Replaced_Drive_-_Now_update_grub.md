---
title: "Replaced Drive - Now update grub?"
date: 2012-08-09
forum: Hardware
---

### Post by subject117 on 2012-08-09
I recently replaced a drive in my mirrored disk array. The smartdisk checks informed me the drive was going to die soon so I replaced it right away. Everything went according to plan, but I am concerned I need to update grub somehow to write the boot sector to the new disk. Is that correct? If so, how do I do that? I do not want to get a nasty surprise when the other drive dies and I can't boot my machine.

```
root@DELL:/boot# sfdisk -l

Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+ 120360- 120361- 966796288   fd  Linux raid autodetect
/dev/sda2     120360+ 121601-   1241-   9963521    5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5     120360+ 121601-   1241-   9963520   82  Linux swap / Solaris

Disk /dev/sdb: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+ 120360- 120361- 966796288   fd  Linux raid autodetect
/dev/sdb2     120360+ 121601-   1241-   9963521    5  Extended
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5     120360+ 121601-   1241-   9963520   82  Linux swap / Solaris

Disk /dev/md0: 241699056 cylinders, 2 heads, 4 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/md0: unrecognized partition table type
No partitions found

```

---

### Post by OM55 on 2012-08-10
Hi subject117,

If you do an image backup (with Image for Linux for example: [http://www.terabyteunlimited.com/image-for-linux.htm](http://www.terabyteunlimited.com/image-for-linux.htm)) than when you restore to the new drive - it will be bootable most of the times without any problems (depends on how complicated the partition structure you have).

BUT, in the odd case that you restored and yet the drive is not bootable, here is how you can reinstall grub successful:

1. Boot with Ubuntu Live CD

2. Open terminal (command prompt)

3. Type: sudo fdisk -l

You will get a list of partisions, similar to the following list:

/dev/sda1 13 102400 de Dell Utility
/dev/sda2 * 13 1926 15360000 7 HPFS/NTFS
/dev/sda3 1926 30892 232676566 7 HPFS/NTFS
/dev/sda4 30893 60802 240245761 5 Extended
/dev/sda5 30893 59584 230467584 83 Linux
/dev/sda6 59585 60802 9777152 82 Linux swap / Solaris 

Ubuntu partition is the one with the name "Linux" (not necessarily the one with the star, although could be).
On this case is on '/dev/sda5' so we have to mount it:

4. sudo mount /dev/sda5 /mnt
   (replace 'sda5' with the partition name in your case)

5. And then install grub:
   sudo grub-install --root-directory=/mnt /dev/sda

6. Reboot and verify that all is working fine.

Hope that helps!

---

### Post by ahallubuntu on 2012-08-10
OM55 has the right idea: repair Grub by booting a Ubuntu live CD.    But because you have a RAID mirror, you will need to mount the array instead of an individual partition.

I have used the "chroot" method of repairing Grub many times and find it very reliable.  I have never done it with a RAID, but these instructions explain how to do it with or without a RAID:

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

You can do this now without waiting for the other drive to fail.  If the live CD you use does not have the mdadm tools installed, just install them during the live session as the instructions describe.  (That also assumes you have a working internet connection during the live session.)

---


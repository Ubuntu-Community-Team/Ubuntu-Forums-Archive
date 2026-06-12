---
title: "Problem mounting fat32 hard drive"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by x-ph on 2007-10-02
All I do is:

xph@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4860    18555075   83  Linux
/dev/sda3            4861        4998     1108485   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3648    29302528+   c  W95 FAT32 (LBA)

xph@ubuntu:~$ sudo mount -t vfat /dev/sdb1 /media/iPod
mount: special device /dev/sdb1 does not exist

This is ordinary hard disk Seagate, which I want to mount and keep synched with my 30GB iPod.
Any ideas what is wrong?

---

### Post by x-ph on 2007-10-02
In addition:

xph@ubuntu:~$ sudo mount -t vfat -o iocharset=iso8859-1 /dev/sdb /media/iPod/
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

xph@ubuntu:~$ dmesg | tail
[   63.696843] Bluetooth: RFCOMM socket layer initialized
[   63.696866] Bluetooth: RFCOMM TTY layer initialized
[   63.696869] Bluetooth: RFCOMM ver 1.8
[  156.955282] FAT: invalid media value (0xb9)
[  156.955292] VFS: Can't find a valid FAT filesystem on dev sdb.

---

### Post by dabl on 2007-10-02
> **x-ph said:**
> 

 which I want to mount and keep synched with my 30GB iPod.


Only a hunch.

FAT32 is a non-journalling filesystem format -- unlike NTFS, ext3, reiserfs, etc., it has no capacity to repair itself if a write operation is not completed for some reason.  It's not a big deal in Windows, until recent times, because older versions of DOS and Windows were always very "sequential" in sending the transaction write commands to the hard drive immediately.

Linux isn't Windows.  Linux schedules transactions, and writing the last command out to the hard drive isn't always the next highest priority task.  Unplugging things from the USB bus in Linux may result in transactions not completed.  That's a very bad thing for a FAT32 formatted drive, because of the lack of journalling.

That may or not be the exact problem in this case, but I wouldn't be betting any important data to a FAT32 device connected to a Linux box via the USB bus .....  :popcorn:

---

### Post by x-ph on 2007-10-02
Thanks for the information, but in this case that is not the problem. I attached this hard disk as it is - formatted in fat32 and with some music on it. It is not damaged. I can mount it when I boot from  ubuntu live cd. The hard is ok. Other suggestions? Thans in advance!

---

### Post by x-ph on 2007-10-03
Is there a way to see haw the HDD is mounted in the live session and to use the same options? Or is there another way of mounting it? Some kind of software that can detect automatically my hard drive?

---

### Post by x-ph on 2007-10-05
Thanks for the help, all of you! ....

---

### Post by dabl on 2007-10-05
Does it show up when you issue```
 blkid
```?

If you could "mount by UUID", it might mount correctly.  My thumb drive is formatted NTFS, but it works when I put it in the computer and then boot the computer.  It doesn't auto-mount when I just stick it in the USB connector while the system is running -- it is recognized, but permissions aren't set to let me access it as a user.

You can find the UUID (assuming it is recognized by the system at all) with this command:

First, ```
fdisk -l
```  (you have done this already)

Then ```
hwinfo | grep 'usb' | grep 'sdb'
```  (sudo apt-get install hwinfo if you need to)


Then get the UUID of that partition (sdb1).


Here's my /etc/fstab line that mounts my USB thumb drive:

```
UUID=A8FC3435FC33FC5E /media/NTFSTICK ntfs-3g user,atime,rw,nodev,nosuid 0 0
```

:)

---


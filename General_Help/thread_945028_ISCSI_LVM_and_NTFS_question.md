---
title: "ISCSI LVM and NTFS question"
date: 2008-10-12
forum: General Help
---

### Post by rhodest83 on 2008-10-12
Okay, not sure if this can be done.

I've setup a logical volume called data that is mirrored.  It is:

/dev/vg0/data

From there, I have setup iscsitarget software, and exposed this logical volume as a LUN.  Then I connected to it from my Vista machine and formatted it as NTFS and am proceeding to use to copy files.

Any ideas on what the best way to make this NTFS drive available to the local ubuntu installation is?

I tried:

mount -t ntfs /dev/vg0/data /mnt/windows

but I get:

NTFS signature is missing.
Failed to mount '/dev/mapper/vg0-data': Invalid argument
The device '/dev/mapper/vg0-data' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Any ideas on the best way to make this data available to the local linux machine?

---

### Post by rhodest83 on 2008-10-12
One answer:

root@top:/mnt# fdisk -lu /dev/vg0/data

Disk /dev/vg0/data: 429.4 GB, 429496729600 bytes
255 heads, 63 sectors/track, 52216 cylinders, total 838860800 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb16d76e

        Device Boot      Start         End      Blocks   Id  System
/dev/vg0/data1            2048   838856703   419427328    7  HPFS/NTFS


root@top:/mnt# losetup -o 1048576  /dev/loop2 /dev/vg0/data


root@top:/mnt# mount -t ntfs-3g /dev/loop2 /mnt -o force


[http://www.redhat.com/archives/linux-lvm/2005-August/msg00063.html](http://www.redhat.com/archives/linux-lvm/2005-August/msg00063.html)

---


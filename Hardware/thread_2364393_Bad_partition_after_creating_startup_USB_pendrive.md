---
title: "Bad partition after creating startup USB pendrive"
date: 2017-06-22
forum: Hardware
---

### Post by joseraeiro on 2017-06-22
Hi,

I'm trying to delete partitions from and get the error "partition doesn't exist".

Here what fdisk -l tells me:

Disk /dev/sda: 74,5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf7b5892b

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 150536191 150534144 71,8G 83 Linux
/dev/sda2       150538238 156301311   5763074  2,8G  5 Extended
/dev/sda5       150538240 156301311   5763072  2,8G 82 Linux swap / Solaris




Disk /dev/mapper/cryptswap1: 2,8 GiB, 2950168576 bytes, 5762048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

-"-

Both Nautilus and Gparted shows partitions on /dev/sdb. Please check the inline printscreens:

[http://imgur.com/a/DS2Qq](http://imgur.com/a/DS2Qq)
[http://imgur.com/a/Hm7Vu](http://imgur.com/a/Hm7Vu)

Thank you very much!

---

### Post by yancek on 2017-06-22
The second image you posted clearly shows that  drive is mounted.  You need to unmount before you make any changes.  Since it is an Ubuntu iso file you could simply create a new partition table for it on GParted.

---

### Post by joseraeiro on 2017-06-22
Thanks for the message!

I've unmounted and the problem persists.

[http://imgur.com/a/SU3zn](http://imgur.com/a/SU3zn)

Thanks again!

---

### Post by yancek on 2017-06-22
If you have the Ubuntu iso file on the usb drive and want to remove it and re-use, use GParted from another system to create a new partition table from the Device tab

---

### Post by joseraeiro on 2017-06-23
Hi guys,

Thanks for your help so far.

So I've booted into Tails Linux and tried to use the application Disks to solve the problem. 

Now the error message is different.

Could you kindly look at the attached files and tell me what you think?

Thanks a million!

---

### Post by yancek on 2017-06-23
I think the most likely solution is to create a new partition table due to the fact that you had an iso on the flash drive since you simply want to remove anything from the flash drive to re-use it.

---

### Post by johndough2 on 2017-06-26
Hi

First thing to strike me was the exit without a clean shutdown.  I get this kind of thing with W10.

Sometimes Gparted can offer and can clean the partition, sometimes I need to revisit and exit cleanly from W10.

The next thing is the block size being mis-reported?

I would just remount and umount using a selection of switches like -n -r before moving onto -f -l

**-n** Unmount without writing in */etc/mtab*. **-r** In case unmounting fails, try to remount read-only. **-d** In case the unmounted device was a loop device, also free this loop device. **-i** Don't call the /sbin/umount.<filesystem> helper even if  it exists. By default /sbin/umount.<filesystem> helper is called  if one exists. **-a** All of the file systems described in */etc/mtab* are unmounted. (With **umount** version 2.7 and later: the *proc* filesystem is not unmounted.) **-t** *vfstype* Indicate that the actions should only be taken on file systems  of the specified type. More than one type may be specified in a comma  separated list. The list of file system types can be prefixed with **no** to specify the file system types on which no action should be taken. **-O** *options* Indicate that the actions should only be taken on file systems with the specified options in */etc/fstab*. More than one option type may be specified in a comma separated list. Each option can be prefixed with **no** to specify options for which no action should be taken. **-f** Force unmount (in case of an unreachable NFS system). (Requires kernel 2.1.116 or later.) **-l** Lazy unmount. Detach the filesystem from the filesystem hierarchy now, and cleanup all

---

### Post by efflandt on 2017-06-26
ISO 9660 indicates that it is obviously an iso image, so just like you cannot remove partitions from CD/DVD, you cannot remove partitions from the device in its current state. Have you tried using gparted to create a new msdos (or gpt) partition table on it? That is what I did if I accidentally formatted the device, instead of a partition on it, with Startup Disk Creator when it used a vfat (FAT32) partition, instead of writing the iso directly to the device like it does now.

An alternative if all else fails is to use dd to write a bunch of /dev/zero to the beginning of the device to make it appear to be empty, then add a new partition table. But you have to know what you are doing and reference the proper device, because the nickname for dd is "data destructor" if you use it improperly (write to the wrong device). Years ago when I accidentally formatted a floppy for Mac instead of msdos (or minix), I could not reformat it as msdos until I wrote some /dev/zero to the beginning of it.

---

### Post by joseraeiro on 2017-06-26
And how can I accomplish that? Gparted on tails doesn't show the option to create a new partition table...

---

### Post by joseraeiro on 2017-06-26
> **yancek said:**
> I think the most likely solution is to create a new partition table due to the fact that you had an iso on the flash drive since you simply want to remove anything from the flash drive to re-use it.

And how can I accomplish that? Gparted on tails doesn't show the option to create a new partition table...

---

### Post by joseraeiro on 2017-06-26
> **efflandt said:**
> ISO 9660 indicates that it is obviously an iso image, so just like you cannot remove partitions from CD/DVD, you cannot remove partitions from the device in its current state. Have you tried using gparted to create a new msdos (or gpt) partition table on it? That is what I did if I accidentally formatted the device, instead of a partition on it, with Startup Disk Creator when it used a vfat (FAT32) partition, instead of writing the iso directly to the device like it does now.



Recreating as a start up disk did the trick!

Thanks a million guys!

---


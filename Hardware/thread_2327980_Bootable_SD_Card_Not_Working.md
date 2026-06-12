---
title: "Bootable SD Card Not Working"
date: 2016-06-16
forum: Hardware
---

### Post by david527 on 2016-06-16
I have an encrypted Ubuntu 14.04 installation on a 16 GB generic SD card. It's worked fine for about a week, but today, it didn't show up as an option to boot. I booted into Windows where it was not recognized. I then booted another Ubuntu live USB to investigate. In Ubuntu disks, it shows up as Device: /dev/mmcblk0 Size: 1.1GB Contents: Unkown. dmesg returns:
```

[ 2159.631143] mmc0: new SD card at address b368 
[ 2159.632166] mmcblk0: mmc0:b368 SMI-S 1.00 GiB

```
The card reader works fine for other cards, and the read only switch is not on. I'm afraid that it may be too late, but any help would be greatly appreciated as the files stored are critically important and were not backed up as recently as they should have been. Thanks!

---

### Post by sudodus on 2016-06-16
Welcome to the Ubuntu Forums :-)

I would suggest that you try to repair the file system, but I don't know how to do it when it is encrypted. Let us hope that someone who knows will read this thread.

Please tell as much as possible about your system: What kind of encryption is it? Encrypted disk (LVM with LUKS encryption), or encrypted home (ecryptfs), or some other kind of encryption?

---

### Post by david527 on 2016-06-16
Thanks!
The installation is an LVM encrypted with LUKS using the installer (default settings). Also, In GParted, a single 1.00 GB unallocated partition is shown with a warning "/dev/mmcblk0: unrecognised disk label".

---

### Post by sudodus on 2016-06-16
We can start with the small end: Try to check/repair the ***boot*** partition, which is not encrypted. It may help, if the problem is there.

Boot from another drive with linux and run

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter and y is the partition number (I think y is **1** for the boot partition).

But if the problem is that the*** encrypted partition*** is bad, I think we have to wait for someone else to help. Of course you could try with the e2fsck command for this partition too and hope it will help, but it might also make things worse, I really don't know.

***A safe alternative would be to make a cloned copy of the drive, the whole 16 GB generic SD card, and try to repair the cloned copy.***

---

### Post by david527 on 2016-06-16
Here is the output:
```
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/mmcblk0
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/mmcblk0

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


```

sudo fdisk -l
```
Disk /dev/mmcblk0: 1073 MB, 1073741824 bytes
4 heads, 16 sectors/track, 32768 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mmcblk0 doesn't contain a valid partition table
```

I did attempt to clone the SD card, but only 1GB is accessible to me.

---

### Post by sudodus on 2016-06-16
**/dev/mmcblk0** is the whole device. You must be able to see a *partition*, for example **/dev/mmcblk01**, or in another adapter maybe **/dev/sdb1**, in order to run ***e2fsck***.

It seems that the partition table is damaged. In this case I think it is important to clone the drive and work on the cloned copy. You can try ***testdisk***, which might be able to identify the partition table.

There is a companion to testdisk, ***photorec***, but I am afraid that it will not work because of the encryption.

[url=https://www.cgsecurity.org/[/url]

-o-

See also this link: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by david527 on 2016-06-16
Yes, I know I need to specify partition, but there are none currently identifiable. I did try 0 and 1, but neither worked. I'll look into the other things you've mentioned and get back.
Thanks!

---

### Post by C.S.Cameron on 2016-06-16
Can you mount the encrypted volume?
Save what you can, maybe copy home.
Google:

How to mount encrypted LVM logical volume

(I have not tried it myself).

---


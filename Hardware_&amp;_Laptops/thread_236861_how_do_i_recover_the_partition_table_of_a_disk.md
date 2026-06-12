---
title: "how do i recover the partition table of a disk?"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by reuben on 2006-08-15
Hello, I reinstalled kubuntu twice over the weekend for various reasons. Each time it didn't detect one of my hard disks (/dev/hdc) during the assignment of partitions stage (although the parted stage did detect it.) The first time around, I was able to add it to my fstab, and get it up and running. This second time I can't get the disk to mount for love nor money. 

I've tried gpart (guessed wrong); fdisk -l (didn't find any partitions); mount (wrong fs type or bad superblock); and adding to my fstab (same problem as mount). The only thing that gaves me a vague glimmer of hope was qtparted (which told me that the partition is hidden, although now it tells me that it is free -- I haven't done anything to modify it.)

I'm running e2fsck on it as we speak and will post the results to this bug. But, my real question here is: how can I get the data off the disk? I don't care about restoring the partition per se. Is there anything I can do at a low level to just get a copy of the data? Naturally I don't have a backup.

Details in this bug: [https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/56341](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/56341)

---

### Post by reuben on 2006-08-15
Joy to the world and sleighbells ring. e2fsck worked. There were a bunch of wrong inode counts etc. OK, I'll forget any lessons learned about backups and proceed :D

---

### Post by irw on 2006-08-15
[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") has saved my bacon before.

On one occasion after spending the best part of a weekend trying to rescue my hard disk after Windows trashed the partition table, this program solved the problem literally within 2 minutes of running it - I was running an Ubuntu liveCD, downloaded, installed and ran it from there.

---

### Post by nmsmith on 2006-08-19
I accidentally have apparently wiped the partition table of a disk. It should contain 80Gb NTFS (unused as I am between windows installations) and 80Gb FAT32 (my main data disk).

Playing with windows installations had wiped grub off the MBR of hda, so my linux partition (hdb2) was not bootable. I tried in grub typing
```
find /boot/grub/stage1
```
and it told me "(hd1,1)", so I continued:
```
root (hd1,1)
```
and
```
setup (hd1,1)
```
However the boot situation was the same. I didn't get any grub menus when booting either disk.

Now gparted claims that /dev/hda (the two 80Gb partitions) is just 160Gb of unallocated space.

I have briefly tried TestDisk, but it does not list the drive as mounted, and I don't know how to mount partitions that aren't apparently there.

I didn't recently back this drive up, as I didn't really expect to have to  play with the MBR, or partitioning.

I'm confused and panicky. Can anyone help?

---


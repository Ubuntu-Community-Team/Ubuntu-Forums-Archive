---
title: "Help!!! Trashed Hard drive"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by markr on 2005-10-11
I could well be labelled an idiot for this one,  but if anyone can dig me out of a hole!!!!!

I have an 80gb USB HDD formatted to EXT3.  I needed to shrink this drive by a couple of gig so I could connect it to a WinXP machine and download some stuff.

I went into Partition Magic,  told it to resize (reduce) by 2 gig and then all hell broke loose.  Partition Magic kicked up some messages about invalid partitions and aborted the resize.  I rebooted my machine and now my 80bg partition is now read as an empty NTFS partition (Please don't tell me about backing up,  I've just found out how important it is!).

I'm hoping that WinXP and Linux are simply reading the partition as NTFS when it's actually EXT3,  but how do I get my HDD to tell the OS's that it's not NTFS at all (perferably without reformatting etc as I'm hoping my data is still intact).

Any help greatly appreciated as I have my entre music collection on it :(

---

### Post by brt on 2005-10-11
what does fdisk tell you about your partitions?

---

### Post by markr on 2005-10-11
fdisk is telling me....

/dev/sda1 - HPFS/NTFS
/dev/sda2 - W95 Ext'd (LBA)
/dev/sda3 - W95 FAT32 (LBA)

It's /dev/sda1 that used to be my EXT3 partition.

---

### Post by brt on 2005-10-11
what happens if you try to mount /dev/sda1 ?

---

### Post by markr on 2005-10-11
If I plug it into the usb port it mounts as /dev/sda1 (type ntfs) which is what I see in mtab.

If I umount it,  it disappears from mtab.

If I try to manually mount it I ge the error

"can't find /dev/sda1 in /etc/fstab or /etc/mtab

If I add the device into fstab I get the following error trying to mount

wrong fs type, bad option, bad superblock on /dev/sda1
missing codepage or other error.

SysLog says "VFS: Can't fint ext3 filesystem on dev sda1"

Thanks for the help so far.

---

### Post by jatos on 2005-10-11
Your best bet to is to look around at the various data recovery tools on the net, find one that has a trial and supports EXT3 (you won't get a reliable data recovery tool), a tool I had good experiences is getdataback but I beleive that only supports FS's that where originally NT and FAT I beleive.

Whatever package you get ensure its got a trial so you make sure you don't pay loads for a useless package.

---


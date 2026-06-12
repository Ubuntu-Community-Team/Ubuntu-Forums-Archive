---
title: "Have Ubuntu 8.10. Have ready partition. Vista no want?"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by antipuls3 on 2009-03-26
Basically, when I was installing Ubuntu, I created 3 partitions. An ext3 for Ubuntu, and 2 NTFS. One is my "TransFiles" drive for use by both operating systems, and the other is for Windows. However when I boot off the Vista disc, it doesn't like that NTFS partition. There's more than 30gb of space there, and I even reformatted the partition, and then deleted it and had the Vista disc create a new partition with the free space. It didn't like it... what should I do now?

---

### Post by Mark Phelps on 2009-03-28
A better approach would be to install Vista first and then Ubuntu.  Ubuntu will see Vista when you install it and create a stanza in grub for you, so that you can dual-boot.

Vista doesn't have to be the first partition (in one machine, I have it on the second), but it does need the first partition to be MS Windows compatible, preferrably, NTFS.

IF your first partition is Ext3, Vista will refuse to install.

---

### Post by antipuls3 on 2009-03-29
> **Mark Phelps said:**
> A better approach would be to install Vista first and then Ubuntu.  Ubuntu will see Vista when you install it and create a stanza in grub for you, so that you can dual-boot.

Vista doesn't have to be the first partition (in one machine, I have it on the second), but it does need the first partition to be MS Windows compatible, preferrably, NTFS.

IF your first partition is Ext3, Vista will refuse to install.

Well... I installed Ubuntu first... and now I have Vista on a separate partition. It killed my grub, so I used Super Grub Disk to restore it. Now I don't see Vista. Can I edit something so I can see both Vista and Ubuntu? You said Vista needs to be on the first partition to be MS Windows compatible.... what exactly does that mean? The partition is NTFS (obivously) and Windows is on it...

I sound like a n00b.

Thanks! :-)

---

### Post by Pumalite on 2009-03-29
Boot your Live CD and from the Terminal, post:
```
sudo fdisk -lu
```

---

### Post by antipuls3 on 2009-03-29
> **Pumalite said:**
> Boot your Live CD and from the Terminal, post:
```
sudo fdisk -lu
```

What will that do?

---

### Post by Mark Phelps on 2009-03-30
> **antipuls3 said:**
> You said Vista needs to be on the first partition to be MS Windows compatible.... what exactly does that mean? The partition is NTFS (obivously) and Windows is on it...
Thanks! :-)

No, I said that MS Windows will attempt to install its boot loader files on the first partition it finds -- and it needs that partition to be a compatible filesystem -- FAT32 or NTFS.  In the case of Vista, I believe it needs that partition to be NTFS.

If you installed Ubuntu to the first partition, it's formatted Ext3 and MS Windows can not (natively) handle that filesystem.

The command you were provided will list your partitions and show the filesystem format of each partition.

---

### Post by antipuls3 on 2009-03-30
> **Mark Phelps said:**
> No, I said that MS Windows will attempt to install its boot loader files on the first partition it finds -- and it needs that partition to be a compatible filesystem -- FAT32 or NTFS.  In the case of Vista, I believe it needs that partition to be NTFS.

If you installed Ubuntu to the first partition, it's formatted Ext3 and MS Windows can not (natively) handle that filesystem.

The command you were provided will list your partitions and show the filesystem format of each partition.

Hmm. I know that my first filesystem is ext3. So I suppose the easiest thing to do would be to format the whole drive, install Vista first, and then Ubuntu, like you said. *sigh*. I don't feel like re-customising my Ubuntu again... but I guess that's half the fun xD

---

### Post by Pumalite on 2009-03-30
> **antipuls3 said:**
> What will that do?
It will let us know what your hrad drive looks like and probably allow people to help you better.

---


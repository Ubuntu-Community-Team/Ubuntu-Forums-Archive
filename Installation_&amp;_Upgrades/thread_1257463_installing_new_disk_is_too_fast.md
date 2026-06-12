---
title: "installing new disk is too fast"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by aic on 2009-09-03
I'm installing a 1.5TB disk in my Hardy system. I was expecting to spend hours formatting and testing the drive. But when I formatted with a GParted live CD, it took about 10 minutes. And to check the disk integrity, I booted into Hardy and typed "sudo fsck -a /dev/sdb1", which took about 10 seconds.

There are no files on this drive yet. I have to think I'm doing something wrong here. Any guidance?

---

### Post by fatbotgw on 2009-09-03
I am by no means an expert, but for a brand new empty drive that sounds about right to me.  Since there are no files to check the integrity of the fsck should go pretty quick.

---

### Post by oldos2er on 2009-09-03
> **aic said:**
> I'm installing a 1.5TB disk in my Hardy system. I was expecting to spend hours formatting and testing the drive. But when I formatted with a GParted live CD, it took about 10 minutes. And to check the disk integrity, I booted into Hardy and typed "sudo fsck -a /dev/sdb1", which took about 10 seconds.

There are no files on this drive yet. I have to think I'm doing something wrong here. Any guidance?

 You created one large partition...? Using which filesystem, ext4, or something else? 

 I switched my partitions to ext4 some time ago, and fsck does run faster now than it did on ext3.

---

### Post by Barijazz on 2009-09-03
Since fsck is a File System Checker and not a physical disk integrity checker, that sounds about right for a clean disk; there aren't any files to sift through.  fsck on my 16GB ext3 SD card is instantaneous, and I have several gigs used.

---

### Post by aic on 2009-09-03
> **oldos2er said:**
> You created one large partition...? Using which filesystem, ext4, or something else? 

 I switched my partitions to ext4 some time ago, and fsck does run faster now than it did on ext3.
Yes. One ext3 partition. This is a file server that has used up its 250GB drive, so I'm moving the home partition to the new 1.5TB drive.

---

### Post by aic on 2009-09-03
I think I may have figured it out. I typed ```
sudo umount /dev/sdb1
sudo e2fsck -c -p /dev/sdb1
```and the disk started cranking for several minutes. I left it running and I'll check it tomorrow.

---

### Post by aic on 2009-09-04
I think it worked. I came back to:```
/dev/sdb1: Updating bad block inode.
/dev/sdb1: 11/91578368 files (9.1% non-contiguous), 2936465/366284000 blocks

```

---


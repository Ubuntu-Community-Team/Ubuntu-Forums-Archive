---
title: "Problems creating ext3 filesystem over 1.3 TB"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by jacobkm on 2005-11-15
Hey folks --

I've got a server with a 3.3 TB RAID5 array (driven by a 3ware 9500 SATA RAID card) and I can't for the life of me get Ubuntu to recognize more than 1.3 TB of it at once.

The installer sees the array and correctly reports it as 3.3 TB; it even lets me create one big partition without reporting any errors.  However, upon the first reboot I'm greeted with a message that the filesystem size does not match the superblock size.  

Running e2fsck gives a big error message about the same thing, but if I force it to run it will happily churn away and finally report no errors.  However, at that point if I mount the disk it has somehow become only 1.3 TB.  

If I try repartitioning the disk with fdisk I'm only allowed to create partitions up to 1.3 TB.  If I try cfdisk it seems to allow me to create a full partition, once I exit cfdisk it's only 1.3 TB again.

I've tried formatting the drive as XFS, ext2, and ReiserFS, and in each case I get the same behavior -- invalid superblock errors which look repairable but result in a loss of 2/3 of the drive.

I *can* make it work if I split the drive into three 1.2 TB partitions (ext3), but that's not really flexible enough in the long run (this is a backup server, and I don't want to have to juggle backup sets to make them fit into artificially small partitions).

(Other possibly sailient bits of info: the machine is a dual-Opteron; I'm using the Breezy AMD64 server install image; the RAID array is composed of 10 400GB disks).

I'm totally stumped -- does anyone have any ideas?

---

### Post by skylark on 2005-11-16
I wish I could afford such a nice array. I don't know the answer but you might get some ideas from this thread: [http://www.gossamer-threads.com/lists/engine?do=post_view_printable;post=583509;list=linux](http://www.gossamer-threads.com/lists/engine?do=post_view_printable;post=583509;list=linux)

The other thing you might try is rolling your own 2.6.14.2 kernel and see what happens?

---

### Post by jacobkm on 2005-11-16
Skylark -- thanks for the pointer.  However, it looks as if the problems in that thread relate to speed issues; my speed is fine, I just can see the whole array.  I don't *think* I need to build a new kernel; examining the stock one shows that large SCSI support is enabled, as are the 3ware 9xxx drivers.

---

### Post by jacobkm on 2005-11-17
Got it!

Turns out that I was doing a few things wrong.  First, I needed to use the "GPT" partition style for my drives; fdisk and friends all use DOS partitions, but "parted mklabel" can make GPT partitions.

That would make the partition work and mount just fine, but upon reboot I would get corrupted filesystem errors.  Turns out that there's an obscure option, CONFIG_EFI_PARTITION, that needs to be set in your kernel to successfully use partitions over 2T (see [https://www.gelato.unsw.edu.au/archives/lbd/2004-November/000071.html)](https://www.gelato.unsw.edu.au/archives/lbd/2004-November/000071.html)).  I recompiled the kernel with that option, and now I'm happily seeing all of the drive!

---

### Post by skylark on 2005-11-17
Glad to hear you persevered and got it working. I think some of your discoveries deserve to go into the Ubuntu wiki somewhere.

---


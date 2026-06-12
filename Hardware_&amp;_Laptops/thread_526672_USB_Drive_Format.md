---
title: "USB Drive Format"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by Fully216 on 2007-08-15
My sister gave me a 1 GB micro center USB drive that is no longer working properly, in hopes that I would be able to fix it.  The only information attached to the drive that might be helpful is possibly a model/part number etched into the end of the USB connector: G01G and MF2690032.

The good news is that she does not care about the data on the drive, so my goal is only to reformat it so it works.  At this point I will settle with any format, but I would prefer FAT32.

I have attempted to reformat the drive in windows by using the format utility found under My Computer > Manage > Disk Management and then selecting format.  It tells me the drive is write protected.  The kicker is, there is no switch to write protect the data on the outside of the drive.

Well, no real surprise there.  I wasn't expecting it to be that easy.

I booted into Ubuntu and this is were things get a bit more interesting.  In the command line, when I type in fdisk -l, I get the following:

Disk /dev/sda: 1014 MB, 1014497280 bytes
32 heads, 61 sectors/track, 1015 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes

Disk /dev/sda doesn't contain a valid partition table

Well, I realized it does not contain a valid partition table, otherwise I would have been able to reformat the drive in windows.

I then try to format the drive using gparted.  I am running it as root.  It shows the drive having 964.84 MB, all unallocated.  I click on Device > Set Disklabel.  I have tried using an msdos label, bsd, and many others.  They all give me the same error; the general and vague "error while setting disklabel."  The bad news is that I cannot format the drive without setting a disk label first.

I have also tried searching online for other tools that might work, of which none have.  There is nothing under mico center's website that would offer any help.

Maybe this is just a lost cause, but I figured I would see what the brilliant people here thought of first before I just trash the drive.

---

### Post by ddrichardson on 2007-08-16
Have you tried fdisk to delete partitions then recreate them? This is what I did with a similar drive last year. Windows wouldn;;t touch it and neither would gparted. There's a howto on my [home]("http://uk.geocities.com/ddrichardson@btinternet.com/recoverusbkey.html") page - obviously ignore the part about kanotix.

---

### Post by Fully216 on 2007-08-17
Okay, I am going through the process now of formating the USB drive with fdisk.  I figured it would be easier to document as I go, that way I can write everything down.

After typing 'sudo fdisk /dev/sda', I get a message back stating,

> Device contains neither a valid DOS partition table, nor Sun, SGI, or OSF disklabel
Building a new DOS disklabel.  Changes will remain in memory only, until you decide to write them.  After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

This is no new surprise.  We already knew it did not have a disklabel for the gparted format attempt.

After typing 'p' to show the partition table, I am given the following:
> 
Disk /dev/sda: 1014 MB, 1014497280 bytes
32 heads, 61 sectors/track, 1015 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes

It does not list a boot device, start, end, block, Id, nor system.  All are blank, as I guess I should expect.  Typing 'o' gives the same warning about building a new DOS disklabel.  When I type 'w' to write the partition table information,

> The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

Good news.  I should have a disklabel now.  Yea!  This victory is short lived however.  When I type 'sudo fdisk /dev/sda' in order to create a new partition, I get the same error as before.

> Device contains neither a valid DOS partition table, nor Sun, SGI, or OSF disklabel
Building a new DOS disklabel.  Changes will remain in memory only, until you decide to write them.  After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Evidentially, the new disklabel was not written.  Grrr.  I try anyway to create a new partition, by selecting 'n'.  I create a primary partition numbered 1, and using the defaults for the first cylinder (1), last cylinder (1015).  I select 't' to change the partition format to 'b', which is W95 FAT32.  When I type 'w' to write the new partition, I get the following:

> The partition table has been altered!

WARNING: If you have created or modified any DOS 6.x partitions, please see the fdisk manual page for additional information.
Syncing disks.

So now I am keeping my fingers crossed it worked anyway.  When I type 'sudo mkfs.vfat -I /dev/sda' I get

> mkfs.vfat 2.11 (12 Mar 2005)

This disk still does not contain a valid partition table according to 'fdisk -l' however.  Grrr!

---

### Post by ddrichardson on 2007-08-17
There is one more thing - it should be /dev/sda1.

If no luck let me know because there is a way to completely overwrite a partition table that messed up but I need to be sure its the correct device.

---

### Post by Fully216 on 2007-08-17
Thanks so much for the quick reply.

No luck using /dev/sda1, as it is 'Unable to open'.

---

### Post by ddrichardson on 2007-08-17
Have  a look at this [post.]("http://mandrivausers.org/index.php?showtopic=41247&st=0&p=316261&#entry316261")

---

### Post by Fully216 on 2007-08-17
Interesting.  Let me know if I did this correctly.  'sudo dd if=/dev/zero of=/dev/sda bs=1M count=2' gives

> 2+0 records in
2+0 records out
2097152 bytes (2.1 MB) copied, 0.1309 seconds, 16.0 MB/s

When I tried to format the drive after that (using the same fdisk procedure), I get the same results.

---

### Post by Fully216 on 2007-08-17
I have found the exact product online, which can be viewed here:

[http://www.microcenter.com/single_product_results.phtml?product_id=0242478](http://www.microcenter.com/single_product_results.phtml?product_id=0242478)

According to that web page, iPSG manufactures the drive.  I have sent them an email ([http://www.ipsgproducts.com/contact/](http://www.ipsgproducts.com/contact/)) asking for help getting the drive working.  I am not sure if they even offer support for their products, but it does not hurt to ask right.

I also sent micro center an email regarding the drive.  I think an attack from both ends is the best plan at this point.

I was hoping to find the actual drive used in the device.  Many times, the manufacturer will offer tools specific to their hardware for fixing problems (Hatichi, Sony, Panasonic, etc all do it).  No luck there, but it was worth a try.

---

### Post by Fully216 on 2007-08-23
I got an email back from Micro Center.  They mentioned that the drives have a limited lifetime warranty.  If you know anything about flash drives, they are extremely robust, and I mean extremely robust.  It is most likely a manufactures defect, in which case they will just swap out the drive.

Thanks all for the help.

---


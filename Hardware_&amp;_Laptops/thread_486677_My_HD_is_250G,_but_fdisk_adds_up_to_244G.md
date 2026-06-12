---
title: "My HD is 250G, but fdisk adds up to 244G?"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by samuraiCat on 2007-06-28
Hi, everybody. I'm experiencing some weirdness with my hard drive. When I use the fdisk -l command, I get this result:
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3648 29302528+ 7 HPFS/NTFS
/dev/sda2 3649 10943 58597087+ 83 Linux
/dev/sda3 10944 11490 4393777+ 82 Linux swap / Solaris
/dev/sda4 11491 30401 151902607+ 83 Linux


So the disk is recognized as being 250G, but the partitions add up to 244G? Where is that other 6G? Gparted says the same thing, by the way.

---

### Post by wjp.reg on 2007-06-28
I believe it's 6 gigs that have gone missing and that is on account of the formatting characteristics (i.e. sector size, bad sectors,etc.)

---

### Post by samuraiCat on 2007-06-28
> **wjp.reg said:**
> I believe it's 6 gigs that have gone missing and that is on account of the formatting characteristics (i.e. sector size, bad sectors,etc.)


Oh, duh--you're right, 6G. Corrected above. So, what do I do about that?

---

### Post by jml on 2007-06-28
I agree.  The formatting process consumes a bit of disc space that is not a problem.  Also, every hard drive has bad sectors on them.  This reduces the total disc space by a small portion.  In the "old days when I used to add hard drives to my computers, the hard drive would come from the manufacturer with a sheet of paper on which was printed a representation of the disc, mapping out the bad sectors.

Joe

---

### Post by samuraiCat on 2007-06-28
> **jml said:**
> I agree.  The formatting process consumes a bit of disc space that is not a problem.  Also, every hard drive has bad sectors on them.  This reduces the total disc space by a small portion.  In the "old days when I used to add hard drives to my computers, the hard drive would come from the manufacturer with a sheet of paper on which was printed a representation of the disc, mapping out the bad sectors.

Joe


Thanks, Joe. So should I just ignore it, or can I recover those bad sectors somehow? I need to reformat and reinstall Fiesty anyway due to some screwups on my part.

---

### Post by jcostom on 2007-06-28
You have fallen prey to marketing, plain & simple..

A gigabyte is widely believed to be 2^30 bytes.  This is false.  A gigabyte is actually 10^9 bytes.  2^30 is a gibibyte.

It has nothing to do with formatting, etc.  It has everything to do with the general public not knowing the difference between a gigabyte and a gibibyte.

Give [http://en.wikipedia.org/wiki/Gigabyte]("http://en.wikipedia.org/wiki/Gigabyte") a read and see.

---

### Post by wjp.reg on 2007-06-28
> **samuraiCat said:**
> Oh, duh--you're right, 6G. Corrected above. So, what do I do about that?

There is nothing to be done.  Formatting took up about 2% of the available capacity.

---

### Post by samuraiCat on 2007-06-28
> **jcostom said:**
> You have fallen prey to marketing, plain & simple..

Those snakes! They're always one step ahead!

---

### Post by samuraiCat on 2007-06-28
> **wjp.reg said:**
> There is nothing to be done.  Formatting took up about 2% of the available capacity.

Oh, okay. Thanks! I wish I could delete posts that won't be useful to anyone later.

---

### Post by amadeus266 on 2007-06-28
The lost space is due to the drive itself storing information about where to find the data stored on the platters. My 250g under windows showed 232g capacity after formatting it new. just like my 40g on this machine only showed 37g capacity. So if you need to store 250g of data you'll need a 300g drive. That's just the way the hardware works.

---

### Post by airtonix on 2007-09-02
no rats....snakes are intelligent and respectful creatures...

rats on the other hand are the sneakiest, disease ridden  filthy scum harvesters there is.

Yes most definitly the Rat....chinese horoscope will describe the rat as a notoriusly selfish creature.

---


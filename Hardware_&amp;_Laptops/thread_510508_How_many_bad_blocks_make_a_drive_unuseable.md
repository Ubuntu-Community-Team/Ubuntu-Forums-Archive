---
title: "How many bad blocks make a drive unuseable?"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by stevehaines on 2007-07-26
I've got a 60 GB drive partitioned with a swap partition, a /home partition, and XP, Ubuntu, Kubuntu, and Freespire installed with multiboot options.

Lately the drive gagged, and I more or less rescued Ubuntu with fsck (though some things are broken). Badblocks returned 129 bad blocks (out of 60,000,000), apparently beginning around 45 GB.

How bad is bad? Should I run "mke2fs -c" before partitioning manually, and do a reinstall without formatting? Or just chuck the drive and buy a new one?

---

### Post by ianare on 2007-07-27
Your drive is fscked up :( .

Salvage what you can and back it up, then transfer to a new drive.

---


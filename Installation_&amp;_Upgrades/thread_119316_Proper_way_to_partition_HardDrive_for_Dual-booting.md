---
title: "Proper way to partition HardDrive for Dual-booting"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by alingatong on 2006-01-19
Hi. I just want to ask this forum for any ideas. I have a Toshiba Laptop A10 with 30 gb hard drive. I am currently doing dual booting with the following partitions:

partition 1: 7 gb, ntfs, winXP (the one that shipped with this laptop)
partition 2: 4 gb, ntfs for data storage of winXP
partition 3: 1 gb, linux swap
partition 4: 7 gb, linux / 
partition 5: 11 gb, linux /home

Is this setup ok as it is? I have read in some articles that frequently doing some re-installs and partitioning will damage the hard disk. when dapper is released in April, I want to do a clean slate--meaning, reformat the hard disk and do an install of winXP and the dapper. I just don't know if there is a better way of partitioning. Once I get dapper installed and winXP, i don't intend to do another round of partition fearing that I might damage the hard disk.

Any ideas?

---

### Post by Topsiho on 2006-01-19
Looks OK to me.

Depends on what you intend to do with it though.

I mean: 11 gb for /home is very difficult to fill it with documents and letters that you write yourself.
But when you put downloaded dvd.iso's there it's another story.

Edit: To me it appears that frequently doing re-installs and partitioning being harmful to your hard disk is just not true.
Nothing more is done than some writing and rewriting to your disk, something it was made for.

Topsiho

---

### Post by az on 2006-01-19
You can partition as many times as you like.  The partition table is just writable space like everything else....


I'm an all-on-one-partition fella myself, but whatever works for you.

---


---
title: "Remove 9.04 to install 9.10 help?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by (null) on 2009-10-30
Two days ago I tried to install Ubuntu 9.04 and it created a separate partition with 50% Windows XP, 50% Ubuntu. But about 52% into the installation process it gives me an error saying that either my cd is burned incorrectly, my laptop is overheating, my hard drive is errored, or my cd drive is failing. After several attempts at installing it (reburning the cd at a lower speed, moving it to a cooler location) I gave up and figured I'd just wait until 9.10 came out in 2 days. 

I tried installing 9.10 and it gives me some mounting error before even starting to install and now I'm thinking that my CD drive is crapping out so I'm trying to just use the exe Windows install. My only problem is that my disk is still partitioned with 52% of 9.04 on it and when I try to install 9.10 from the exe it only lets me install it on the windows partition of my disk. 

tl;dr how do I unpartition the space my failed linux attempts left so that I can have 100% hard drive space again?

I'm not a complete idiot, I'm just new to this whole partitioning aspect. So any help would be much appreciated, I am very determined to install Ubuntu :)

---

### Post by coffeecat on 2009-10-30
Boot up with the 9.10 live CD (if your possibly failing CD drive lets you), and then go to System > Adminstration > Gparted. That's the Partition Editor. Once it's started up it will show the partitions in your hard drive. There will probably be two Linux partitions - one with the ext3 (or ext4) filesystem and one swap. You can use Gparted to delete both - just remember to click on the "Apply" button otherwise your changes won't be actioned.

It could be that the 9.04 partitioner set up an extended partition with one or both of the Linux partitions in logical partitions in the extended. Your best plan would be to delete the extended partition as well, leaving about half the HD as "unallocated" which you can then direct the 9.10 installer to install to.

Be careful when deleting partitions. Manufacturers can sometimes put somewhat obscure partitions on the HD as part of their Windows restore process. In my Sony laptop, the first partition is the Windows restore, and the second the Vista C: - which is fairly straightforward - but I've read of some weird and wonderful manufacturers' partition layouts. If you are at all in doubt, just post a screenshot (Print key or Alt+print for active window only) of Gparted from the live CD.

---

### Post by (null) on 2009-10-30
> **coffeecat said:**
> Boot up with the 9.10 live CD (if your possibly failing CD drive lets you), and then go to System > Adminstration > Gparted. That's the Partition Editor. Once it's started up it will show the partitions in your hard drive. There will probably be two Linux partitions - one with the ext3 (or ext4) filesystem and one swap. You can use Gparted to delete both - just remember to click on the "Apply" button otherwise your changes won't be actioned.

It could be that the 9.04 partitioner set up an extended partition with one or both of the Linux partitions in logical partitions in the extended. Your best plan would be to delete the extended partition as well, leaving about half the HD as "unallocated" which you can then direct the 9.10 installer to install to.

Be careful when deleting partitions. Manufacturers can sometimes put somewhat obscure partitions on the HD as part of their Windows restore process. In my Sony laptop, the first partition is the Windows restore, and the second the Vista C: - which is fairly straightforward - but I've read of some weird and wonderful manufacturers' partition layouts. If you are at all in doubt, just post a screenshot (Print key or Alt+print for active window only) of Gparted from the live CD.
 
Yeah thanks a lot, that did the trick. Before your post I was tinkering around in the install menu manually editing partitions, which left my Windows partition and a bunch of free space. But the real problem was when I was trying to edit my Windows partition to make it take up the free space, it kept giving me an error saying that partition cannot exceed hard disk space when it was telling me that was how much space I had D:

Gparted was merely dragging the partition resize bar and it repartitioned my drive in only a minute. Very user friendly :)

---

### Post by coffeecat on 2009-10-30
> **(null) said:**
> Very user friendly

That's Ubuntu Linux for you! :wink:

---


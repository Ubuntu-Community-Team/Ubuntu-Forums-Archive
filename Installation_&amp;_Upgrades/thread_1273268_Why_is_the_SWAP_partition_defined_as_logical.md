---
title: "Why is the SWAP partition defined as logical ?"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by emma_peel on 2009-09-23
Hello.

I have installed Kubuntu using the standard install protocol (full drive) and I have noticed that the SWAP partition has been defined as a logical partition (sda5).

I now would like to create several partition, but I am limited due to this set-up. I cannot create additional logical partition and the 2 last physical partitions are not enough for my purpose.

Do you know why it has been done such a way ? Does anybody see a problem if I change that ?

Thank you for the feedback.

---

### Post by wpshooter on 2009-09-23
It is probably done this way by default so that your primary partitions will not be used up for the SWAP partition.

However, I generally make all of my partitions primary and not logical.

But if you have a number of installations that you want to do per hard drive, then you would want to have 1 primary partition for each installation and then use logical partitions under that primary so you could save your remaining available primary partitions for other O/S installations.

---

### Post by bumanie on 2009-09-23
A hard drive can have a maximum of 4 primary partitions. One of these can be a logical partition which in turn, is not limited as to how many partition its holds, the only limiting factor is the space available. A logical partition can usually be expanded into unallocated space with a partition editor like gparted, then you should be able to add extra partitions within the logical partition. This does not exactly explain why /swap has been made into a logical partition - I always do manual partitioning, so aren't sure whether this is the standard way the automatic partitioner partitions drives upon installation. This may help you with using [gparted]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html").

---

### Post by oldfred on 2009-09-23
In resizing your partitions you can temporarily delete the swap partition and resize your other partitions, just remember to recreate it before you are done. Windows and a few other systems are the only one's requiring primary partitions. Linux is fine in either primary or logical partitons inside the extended partiton.

---


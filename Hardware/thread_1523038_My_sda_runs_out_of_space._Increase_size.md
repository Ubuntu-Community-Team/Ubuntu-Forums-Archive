---
title: "My sda runs out of space. Increase size?"
date: 2010-07-03
forum: Hardware
---

### Post by dreamquartz on 2010-07-03
Can I increase my sda on my Eeepc?
I have hardly any space left on my laptop for more software.
I have over 30 gb not used on my sdb, but do not see if gParted can do anything.

---

### Post by dreamquartz on 2010-10-07
> **dreamquartz said:**
> Can I increase my sda on my Eeepc?
I have hardly any space left on my laptop for more software.
I have over 30 gb not used on my sdb, but do not see if gParted can do anything.

I asked this a while back and have been experimenting a bit, but to no avail.
I boot up from usb stick, use gparted, and still unable to Unmount sda1.
Anyone any suggestions?

---

### Post by drs305 on 2010-10-07
Here is a post I wrote about expanding /. 
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Of course changing the size of / requires that the Ubuntu partition be unmounted. One of the things that often gets overlooked is that the Gparted LiveCD and others may leave the **swap** partition mounted. Make sure all partitions, not just the Ubuntu one, are unmounted.

To unmount the swap partition, highlight it and then select "Partition, swapoff".

No partitions should have a "key" icon next to them in the lower pane of Gparted. The "key" symbol means the partition is still mounted.

---

### Post by dreamquartz on 2010-10-10
Thx Drs305.

It gave me a bit of an idea, but so far no success.

Does anyone know how to use sdb to increase sda?
I have plenty of room on sdb, and sda is running thin.
Swapping won't work either. That's how much room I've left.

---

### Post by dreamquartz on 2010-10-18
> **dreamquartz said:**
> Can I increase my sda on my Eeepc?
I have hardly any space left on my laptop for more software.
I have over 30 gb not used on my sdb, but do not see if gParted can do anything.

I did a full re-install, using sdb (30 Gb) instead of sda (10 Gb) with a few issues after that, but so far so good.

---


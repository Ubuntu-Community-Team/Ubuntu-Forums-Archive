---
title: "Questions about Raid and LVM"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by madtinkerer on 2006-11-05
Hi,

I'm a little confused about Raid and LVM.  I've been reading lots of howtos, but I can't seem to get any direct answers to my questions.  Can you help me out?

First, I have a hardware raid card (sil 3124 chipset) in my computer and 2 identical 320GB sata drives plus another 300Gb Sata drive.  Should I use software raid or hardware raid in my setup?  I don't even really have to use raid with LVM, do I?

Second, I want to span the 320gb drives into one large partition using lvm first, copy data from the 300gb to them, and then add the 300gb drive to the partition.  Can I add a physical drive to an LVM partition after it has already been setup?

---

### Post by ape on 2006-11-06
1. I would stick with the hardware raid.  You should get much better performance that way.

No, you don't need to use RAID technology to make use of LVM, the two are mutually exclusive.

2. Yes, you can do this.

---

### Post by madtinkerer on 2006-11-06
Thanks for the answers.  Now, I'm really not all that interested in increased performance for this file server, I just want stability.  That being the case, what should I do about the raid?  Should I join the two identical drives in a raid array and build lvm on top of that so I can add in the other drive to the lvm at a later date, or should I just skip raid and build the whole system just with lvm?

---

### Post by ape on 2006-11-06
I think I would still stick with the RAID.

---


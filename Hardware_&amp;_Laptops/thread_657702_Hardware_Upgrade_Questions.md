---
title: "Hardware Upgrade Questions"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by atjensen11 on 2008-01-03
I have Ubuntu 7.10 Server edition running on a Dell Optiplex.  The box currently has a 60 GB hard drive, one network card and a plain CD drive.

I recently acquired a new LG DVD internal writer, a Seagate 250 GB internal hard drive and a new Linksys network card.

I am still fairly new to Linux and therefore am unsure on how to go about installing my new hardware.  Will Ubuntu recognize these items out of the box (DVD and network card)?  I know the hard drive will take more work with adding a partition or something and mounting it.

Anyhow, I am looking for some advice on someone who has done something similar and what pitfalls I should try to avoid.

Thanks.

---

### Post by Fred_E _krugar on 2008-01-03
Yes it should automatically recognize them. But you will have to format the new harddrive  with Gparted.

 You may have a small problem with the linksys card, just depends on what model it is.

---

### Post by ryanVickers on 2008-01-03
all wireless has problems nearly all the time :p

its just a fact of life so far sadly... lol but I got mine working with no trouble

---

### Post by atjensen11 on 2008-02-17
I have only upgraded part of my system.  I installed the CD/DVD writer with now problems at all.  It was recognized and usable instantly.

However, I am holding off on the hard drive upgrade because I am not confident on how I want to proceed.

Currently, my server only has one 60 GB drive.  I have a new 250GB drive waiting to go in.  My current 60 GB drive primarily uses one large partition for all the data.

I realized I will probably have to create/modify some kind of partition on the new 250 GB drive.  So I don't think I can just use dd or something similar to copy the contents of the 60 GB to the 250GB.

In the end, I would likely have two drives with the 250 GB being the master.

Any suggestions on how I should proceed?

---


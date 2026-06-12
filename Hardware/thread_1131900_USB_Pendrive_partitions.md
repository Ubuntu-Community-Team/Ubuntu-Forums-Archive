---
title: "USB Pendrive partitions ???"
date: 2009-04-21
forum: Hardware
---

### Post by sidewalkcynic on 2009-04-21
I have partitioned my 1Gb pendrive into two partitions, however, I am unable to access the number 2 partition.

What I want to do is store archive documents in the 2nd partition - while keeping current documents in the 1st partition.

Is this possible?

---

### Post by Kobalt on 2009-04-21
Absolutely possible. How did you partition your USB key?

---

### Post by abakus on 2009-04-21
If you want to do that like a pro, i mean if your priority is to safe documents from other people the best way to create partition is with PGP and you can activated and deactivate that partition with simple scripted key password

---

### Post by sidewalkcynic on 2009-04-21
> **Kobalt said:**
> Absolutely possible. How did you partition your USB key?
Well, I used the fdisk /dev/sdb

and partitioned 1 - 450, & 451 - 1022

---

### Post by sidewalkcynic on 2009-04-21
> **abakus said:**
> If you want to do that like a pro, i mean if your priority is to safe documents from other people the best way to create partition is with PGP and you can activated and deactivate that partition with simple scripted key password
Well, I wasn't set on getting fancy, but I'll check it out.

---

### Post by sidewalkcynic on 2009-04-21
Well, I think I figured it out:

After partitioning, each partition has to be re-formatted.

---


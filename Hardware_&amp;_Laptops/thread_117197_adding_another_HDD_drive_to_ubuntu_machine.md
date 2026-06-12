---
title: "adding another HDD drive to ubuntu machine"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by vinthund on 2006-01-14
hello,
how do I add a new HDD drive to a ubuntu machine? Well, it is not new, in fact it comes from a broken computer. I Would just like to be able to read/write to it. It has 2 partitions with windows millenium.

Currently I have a HDD with dual boot ubuntu/win98, if that matters.

regards,

vin

---

### Post by aysiu on 2006-01-14
Install it first.
Then boot up into Ubuntu and post the output of these three commands: ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by vinthund on 2006-01-16
[QUOTE=aysiu]Install it first.
Then boot up into Ubuntu and post the output of these three commands: ```
sudo fdisk -l
df -h
cat /etc/fstab
```[/QUOTE]

I do not have the machine at my home so it may be problematic to post, I'll try. Anyway, it is a new install, HDD is inserted in a slot in fron of the machine.... well, without opening the machine, you know.

---


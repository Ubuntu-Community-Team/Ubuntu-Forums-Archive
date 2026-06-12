---
title: "partitioning question"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by bilalakhtar on 2009-02-03
hello everyone,
I have a small question:p:p
I am currently usin Windows XP Pro Sp3. I have 2 partitions, C & D. Windows is installed on C. It does not have enough free space to install Ubuntu. So I will install it in a dual-boot mode(not wubi), taking 10GB of free space from D which currently has 25GB free space. I will have to use the manual method of partitioning rather than the guided ones for this task. I will create a 2GB swap and 8GB ext3 for ubuntu ( no home drive). Can anyone tell me step-wise how to do it?
Will I have to specify a mount point for the two windows partitions? will I have to enter some advanced settings at the final step to make GRUB detect windows?

---

### Post by howefield on 2009-02-03
You might find it easier to load up the live cd and using partition editor from the system > administration menu, resize your D partition to leave 10 gigs for Ubuntu, then tell the installer to use the largest free space.

Hope that makes some sort of sense.

---

### Post by bilalakhtar on 2009-02-03
> **howefield said:**
> You might find it easier to load up the live cd and using partition editor from the system > administration menu, resize your D partition to leave 10 gigs for Ubuntu, then tell the installer to use the largest free space.

Hope that makes some sort of sense.

please anyone tell me a way which does not require using gparted and requires using the manual option while installing ubuntu. have some popcorn:popcorn:.

---

### Post by Pumalite on 2009-02-03
'Manual' 'uses' Gparted. What do you want to do?

---


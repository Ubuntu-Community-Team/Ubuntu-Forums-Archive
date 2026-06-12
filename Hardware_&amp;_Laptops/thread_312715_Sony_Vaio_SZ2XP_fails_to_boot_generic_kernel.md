---
title: "Sony Vaio SZ2XP fails to boot generic kernel"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by thumper on 2006-12-04
I have a sony vaio SZ2XP that had both cores identified with dapper, but on upgrading to edgy I started hitting problems.

It boots fine with the 386 kernel, but that only uses one core.  If I select the generic kernel from the grub menu it just hangs before even getting to the splash screen.

Ideas?

---

### Post by thumper on 2006-12-05
> **thumper said:**
> I have a sony vaio SZ2XP that had both cores identified with dapper, but on upgrading to edgy I started hitting problems.

It boots fine with the 386 kernel, but that only uses one core.  If I select the generic kernel from the grub menu it just hangs before even getting to the splash screen.

Ideas?

I was pointed to [https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/69199](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/69199)  by the canonical support guys, and I followed the instructions there, and voila, boot successful.

Happy camper now :)

---

### Post by ntetreau on 2006-12-11
Hi thumper,
I was wondering if you could expand a bit on how you fixed your problem.  I mean, if you can boot up, how can you run the commands to install the libata module?  Thanks.

Nic

P.S.:  Since I am getting a vaio sz3 in the next few days, I would like to know how to go around this bug.

---


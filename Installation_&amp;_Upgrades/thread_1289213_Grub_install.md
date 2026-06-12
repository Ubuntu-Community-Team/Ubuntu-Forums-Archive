---
title: "Grub install"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by danijanuvary on 2009-10-12
I have two ubuntu 8.10 in my laptop.in /dev/sda3 and /dev/sda9.The grub loader is in /dev/sda3.I need to change the grub loader to /dev/sda9.i used grub-install but it is not working.Can anybody help me???????

---

### Post by VMC on 2009-10-12
> **danijanuvary said:**
> I have two ubuntu 8.10 in my laptop.in /dev/sda3 and /dev/sda9.The grub loader is in /dev/sda3.I need to change the grub loader to /dev/sda9.i used grub-install but it is not working.Can anybody help me???????

output sudo fdisk -l

You can chroot to the desired ubuntu partition and install grub that way. But then if you boot off the sda9 partition that should work. Are you sure you it didn't work?

---


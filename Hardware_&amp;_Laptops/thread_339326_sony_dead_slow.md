---
title: "sony dead slow"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by stevewabc on 2007-01-15
hello all I just install ubuntu 6.10 on a sony vgn-s460 laptop and ubuntu takes 5 min to boot up when its pluged into a/c power. were do I start to look for the problem.. under battery power boot up is 1min... and when loged into gnome runs ok but udder a/c power anything you open takes some time to open...


Please help with this or is this a sony problem?

---

### Post by splezunk on 2007-01-22
I have the same problem when running off power.

I added **acpi=off**  into the grub line when booting or using the AC power.  Problem with this is that you need to either use power with no acpi or acpi and reboot to no acpi when you switch to power.

I have not found a complete solution yet.

---


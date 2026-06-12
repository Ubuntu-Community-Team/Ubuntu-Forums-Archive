---
title: "after loading ubuntu7.04, cdrw/dvd fails to read"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by a3teck on 2007-06-25
laptop is compaq presario 2190us.after loading fiesty fawn the cdrom failed to read. passing no_acpi to the kernel allowed reading the cdrom. Finding the info to make this permanent wasn't easy. Here It is. log in as root. open a text editor. Open file "/boot/grub/ menu.lst" . Find the line starting with "defoptions=" and add no_acpi to this line. This worked for me and I hope it helps someone else.

---


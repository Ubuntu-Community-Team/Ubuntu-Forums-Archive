---
title: "Grub Error 17"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by flameo993 on 2009-01-04
This morning after deleting the Ubuntu partition of my dual-boot Ubuntu and XP laptop, I rebooted and after the BIOS came up, I got this error message where the bootloader screen usually is:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17


I think when I deleted my Linux partition, I deleted with it the files that GRUB needed to boot. How can I get rid of GRUB completely? It doesn't seem like I can get into Windows XP.

---

### Post by flameo993 on 2009-01-04
I can still boot into a CD if that helps

---

### Post by caljohnsmith on 2009-01-04
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
That will install a Windows equivalent MBR into your sda drive so you should be able to boot straight into Windows. Let me know how it goes or if you run into problems.

---


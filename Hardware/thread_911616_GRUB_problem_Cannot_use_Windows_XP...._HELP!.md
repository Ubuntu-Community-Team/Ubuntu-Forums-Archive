---
title: "GRUB problem: Cannot use Windows XP.... HELP!"
date: 2008-09-05
forum: Hardware
---

### Post by shgadwa on 2008-09-05
Here is my story:

I have a Dell Inspiron 8200 laptop, 1.8Ghz, 1GB RAM, 60GB Hard Drive.

I installed Xubuntu on it a couple weeks ago.

A few days ago, I installed Windows XP Pro on it. Then, that made it so that Linux did not boot up. I put the linux installation disk in and booted it in rescue mode, installed the GRUB boot loader, rebooted and WALLA! Linux works.

However, the windows XP partition is not showing up in the boot loader and I cannot boot from it. I tried using the Super Grub Boot Disc, but that did not help as I hoped it would.

Any help would be appreciated.

Shawn

---

### Post by falcon61102 on 2008-09-05
If you could, run and post the results of:
```
sudo fdisk -l
```
-l is a lower case L

That will show all your partitions and drives so we can know a little more about your system.

---

### Post by shgadwa on 2008-09-06
OK.... I will try that. Thanx

---


---
title: "Dual Boot Grub Problem"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by JHSheridan11 on 2008-12-16
I just installed ubuntu 8.10 on a box that already had a windoze XP partition on it. I booted the live CD, and resized the windows partition in half. I then used the free space to have 20gb for /, 20gb for /home, 1gb for swap, and the rest for /opt. Now I cannot see windows when in grub. Anyone have any ideas?

Thanks in advance,
John.

---

### Post by Pumalite on 2008-12-16
Edit menu.lst and add an entry for Windows at the bottom:
title  Windows
root  (hd0,0)
savedefault
chainloader +1

(run sudo fdisk -l and find out what the Windows partition is for sure. Some laptops have a Recovery partition in (hd0,0)

---


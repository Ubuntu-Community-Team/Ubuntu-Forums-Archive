---
title: "External hard drive problem"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by drdmgee on 2008-01-25
I have a dual-boot installation of Ubuntu 7.10 on a PC with an external hard drive (Seagate Free Agent).  The problem is accessing the drive from within Ubuntu.

Sometimes the icon for the drive in Gnome  appears once; sometimes it appears twice. The entry in /etc/mtab is always the same, however, and it only appears once in the Places menu.

When the icon appears only once, everything is OK. When it appears twice, I can't access the drive, even from the terminal, getting an input/output error. The number of icons and the working of the drive appears to be purely random. The drive always works fine from within Windows.

The odd thing is, from within the Live CD version of Ubuntu, the drive always seems to be OK.

Any suggestions?

---

### Post by eredhuin on 2008-01-25
Can you post the contents of your /etc/fstab file?

---


---
title: "Do not mount Windows partition"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by dox_drum on 2009-02-11
Hi there!

Yesterday I've installed Intrepid to a computer with windows, as a dual-boot. However, with I enter to linux, the windows point is not mount.

How should I do for linux to mount that point at startup?

Thank you so much.

[CENTER]Enjoy![/CENTER]

---

### Post by x33a on 2009-02-11
open a terminal and type sudo ntfs-config.

if it's not installed then

sudo aptitude install ntfs-config.

you can use this to mount windows partitions at startup.

---

### Post by Mark Phelps on 2009-02-11
I've found that it's better to use NTFS-3G to mount Windows partitions.  The package comes with modern Ubuntu distros and you only need to change the mount command to indicate type of ntfs-3g.

Also, if you're mounting your Windows OS partition read/write and you have an abnormal shutdown, don't be surprised if Windows will no longer boot.  Be sure to have some Boot media, or a way to boot into Windows and run chkdsk if that happens; otherwise, Windows will remain unusable after that.

---

### Post by dox_drum on 2009-02-12
Thank you both. Asap. I'll try your advices, 'cause the computer is not mine.

[CENTER]Enjoy![/CENTER]

---


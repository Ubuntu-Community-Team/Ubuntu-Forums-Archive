---
title: "Multi boot Grub: which O/S responsible to update it on kernel upgrades ?"
date: 2008-10-11
forum: General Help
---

### Post by Browser_ice on 2008-10-11
I have a multi-boot home PC (see signature). I am starting to wonder about something. The actual Grub used on boot time is the one created by the last O/S I installed.

But I am starting to wonder what will happen if my other Linux O/S have major upgrades causing them to try to update the grub. Will they update the grub on their partition (not used by boot) or will they try to update the real booting grub ?

In other words, I want my real booting grub to always reflect the last booting infos of all my O/S no matter the upgrade they did. Is that possible ?

---

### Post by OutOfReach on 2008-10-11
I'm not too sure, but I think the OS (Linux OS) will update *it's* menu, which is not necessarily the main GRUB menu.

---

### Post by Browser_ice on 2008-10-11
> **OutOfReach said:**
> I'm not too sure, but I think the OS (Linux OS) will update *it's* menu, which is not necessarily the main GRUB menu.

Therefore, the real booting grub will be pointing to the old O/S's kernel. That's why I want to know how to have that real booting Grub with all updates of all O/S at all times.

---

### Post by lswb on 2008-10-11
Take a look at this site, the author often posts on this forum also:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Look for the section where he describes using a "grub partition"

A very small primary partition (I use 100MB, 50 is probably more than enough) is used to hold the grub bootloader that the MBR points. This is NOT a "boot partition", the kernels for each distro will reside on their own / filesystems. The menu.lst in this small partition will use chainloader statements to transfer boot to other bootable partitions. Those other partitions will have their own grub (or some other boot loader) installed. Each distro will update its own menu.lst without affecting the others. The website describes it very well.

---

### Post by lswb on 2008-10-11
...................

---

### Post by bodhi.zazen on 2008-10-11
The hermanzone site is very good.

There are a few suggestions here as well :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---


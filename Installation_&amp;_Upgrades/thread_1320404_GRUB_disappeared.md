---
title: "GRUB disappeared"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by upapilot on 2009-11-09
Hi all,
i used to run Vista and ubuntu 9.04 on dual boot. However about 2 days ago, i upgraded to windows 7 and while doing so, winodws 7 replaced the GRUB menu.....now i want to upgrade to ubuntu 9.10 but dont know how to....i was thinking of deleting the ext3 partition with the LiveCD partition editor then create a new partition to install ubuntu 9.10....please tell me how i should proceed
thanks:)

---

### Post by dstew on 2009-11-09
> i was thinking of deleting the ext3 partition with the LiveCD partition editor then create a new partition to install ubuntu 9.10That sounds like the right plan to me. The new Ubuntu distribution will install grub 2, which is an improved boot loader that should detect and boot your Windows 7 installation as well as your new Ubuntu installation.

You do realize, of course, that if you delete your old ext3 partition that all your files in your old Linux installation will be gone. Make sure you back up the files you want to save before deleting the old partition.

---

### Post by upapilot on 2009-11-10
ok thanks.....i manged to repartition and reinstall ubuntu

---


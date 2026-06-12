---
title: "fresh windows install deleted grub!"
date: 2008-09-01
forum: General Help
---

### Post by furry_freak on 2008-09-01
A couple of weeks ago is set up a dual-boot on a new hdd with ubuntu (newest version), and 64-bit XP which i borrowed from a friend. After windows gave me nothing but grief with drivers etc (as opposed to ubuntu which worked perfectly out of the box), I decided to get my old win 2000 cd out and overwrite the xp install ... long story short, grub's gone, and the windows cd's think the old windows partition's damaged and refuse to install onto it. the linux partition (ext3) is still fine (used the live cd to check), and has all the backups from the old windows install.

1) is there a way to restore grub using the live cd?
2) can i use the live cd's boot command-line options to boot into the existing ext3 partition (and if necessary/possible restore grub from there)?

Thanks
-furry_freak

---

### Post by rouben on 2008-09-01
I think you will find [this howto]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") handy. :)

---

### Post by WRDN on 2008-09-01
You need to follow [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") guide to restore GRUB from the LiveCD.

---

### Post by furry_freak on 2008-09-01
thanks!

---


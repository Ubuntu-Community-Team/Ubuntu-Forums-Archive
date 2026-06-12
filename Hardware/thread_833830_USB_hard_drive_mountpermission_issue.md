---
title: "USB hard drive mount/permission issue"
date: 2008-06-18
forum: Hardware
---

### Post by dancingtofu on 2008-06-18
Hello, all!

Using Xubuntu 8.04 on my ASUS eeePC 701. I know there are eeePC specific forums, but I believe this is a more general issue. I have a 160GB WD Passport USB hard drive. Ubuntu was having trouble mounting at first, but I finally was able to format it to FAT32 (LBA) and now it mounts, but it mounts at /media/cdrom0 and I cannot change ownership or permissions. I can only use it as root. My questions are: Can I change its mount point? How do I find out how linux sees the device itself (such as /dev/sdc1 /dev/sdb1, etc)? Would changing its mount point allow me to grant ownership to the user-level with read and write privileges? Any info is appreciated!

---

### Post by Odrodzona-Sarmacja on 2008-06-21
You need to change in "gksudo gedit/etc/fstab" (gedit/mousepad/kate) the "defaults" in the root only harddrives you want to access as user to "nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000".

Good luck!

---

### Post by dancingtofu on 2008-06-23
Thank you so much! That solved my problem! Much appreciated!

---


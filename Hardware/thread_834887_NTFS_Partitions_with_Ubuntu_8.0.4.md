---
title: "NTFS Partitions with Ubuntu 8.0.4"
date: 2008-06-19
forum: Hardware
---

### Post by balanscott on 2008-06-19
What user permissions do I need to associate to my account (developer) so I can see any NTFS partition? I cannot mount them even after installing NTFS-3g as it says I do not have permissions.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Actually you need to associate permissions to your hard drives and not to your account. The easiest way is to set them up in your fstab and have them automounted or if they are removable then you can have them mounted with "sudo mount -a" after connecting them to your computer with fstab set up corectly with permissions for them. Try
"nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000"
for options. Works for me. The "Uid=..." there is targeting accounts if you like to play with it.

Have fun!

---


---
title: "Mount Partition on Startup?"
date: 2008-07-17
forum: General Help
---

### Post by Ewzzy on 2008-07-17
I have a fat 32 partition that is shared between my ubuntu and windows installs.  I have no problem reading it, but I have to open it to mount it.  This poses a problem with opening media players and setting up sharing through samba.

Could someone tell me how to mount this partition on startup?

---

### Post by Rocket2DMn on 2008-07-17
Yes, it will need an entry in /etc/fstab, you can please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by bodhi.zazen on 2008-07-17
You need an entry in fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by jonian_g on 2008-07-17
Install "Storage Device Manager" from add/remove and you will be able to mount any partition you want. After installation it is at System>Admin>Storage Device Manager.
Click the "Assistant" button to enable automount on boot, have write permissions etc.

---


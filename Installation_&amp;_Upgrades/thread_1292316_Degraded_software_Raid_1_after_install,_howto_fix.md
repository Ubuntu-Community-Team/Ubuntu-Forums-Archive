---
title: "Degraded software Raid 1 after install, howto fix?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by JesperA86 on 2009-10-15
Hi!

I followed this guide: [https://help.ubuntu.com/community/Installation/SoftwareRAID#Updating%20startup%20script](https://help.ubuntu.com/community/Installation/SoftwareRAID#Updating%20startup%20script)


It works great but after the installation and the computer restart it ask me if i want to start in degraded mode, i choose "YES" and the computer starts but it only uses one of the disks in the Raid1 array!

Why is that and how can i fix it?

---

### Post by PeterK2003 on 2010-01-03
I have the same problem!

---

### Post by BLuFeNiX on 2010-08-04
1) Open Disk Utility
2) Find the array and click "edit components"
3) Remove the disk that is "Partially Synchronized"
4) Click "Add spare" and select the drive you just removed.
5) Let it sit for a few hours
6) ???
7) PROFIT!!!

---


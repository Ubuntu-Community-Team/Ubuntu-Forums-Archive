---
title: "Installer doesn't see any partitions"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by richiewrt on 2009-11-10
I am currently trying to install 9.10, but the install see's my HD as one big unallocated partition. I have tried using a gparted live cd (0.3.7-7) and it has the same problem. There should be 3 existing partitions on the drive. 2 for a win7 beta build (one is the actual partition the other is a 100mb partition that the win7 install apparently created. The 3rd partition should be an empty simple partition created with the win7 partition tool. Also I can see the partitions in the ubuntu file manager. Any thoughts or if anyone could point me in the right direction i would be much appreciative.

---

### Post by Mark Phelps on 2009-11-11
Go back into Windows 7 and remove the third partition.  Then, create it again but do not format it.  When you boot from the Ubuntu LiveCD, use that to format the partition as Ext4.  

When you reboot to install, use Manual Partitioning.  It should now see the Ext4 partition you created earlier.

---


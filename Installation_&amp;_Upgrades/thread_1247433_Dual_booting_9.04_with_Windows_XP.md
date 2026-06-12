---
title: "Dual booting 9.04 with Windows XP"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by J A Smith on 2009-08-22
Hi all, 

I am having a problem with partitioning Windows XP for a friend, so that I can install 9.04 in the free space. In the partition manager in Ubuntu setup it shows the Windows XP partition taking up all of space in the HDD (there is at least 40GB free however), which is correct. When I try to shrink the volume and go to 'edit partition' and then select the size I want; I want 20GB, so type in 20000mb, set it to /home. When I click to continue it tells me the size is too small.

In Windows XP itself, Disk Manager will not let me resize the partition. The tutorials I have seen tell me to select free space and create partition, not how to shrink the existing Windows Partition. I have also tried a command line prompt, to no avail.

Any ideas? :confused:

Thanks in advance for any help!

---

### Post by Partyboi2 on 2009-08-22
Hi, boot to the Ubuntu desktop on the live cd and open gparted (System>Admin>Partition Editor) then try using the 'resize' function to shrink down xp. If you want you can also create the necessary partitions for Ubuntu,  then run the installer and either use the partitions you created with gparted (choosing the 'manual' option at the partitioning stage to set the mount points) or choose the option to use the unallocated space.

---

### Post by J A Smith on 2009-08-23
Perfect Partyboi, worked first time!

Thank you very much. :)

---


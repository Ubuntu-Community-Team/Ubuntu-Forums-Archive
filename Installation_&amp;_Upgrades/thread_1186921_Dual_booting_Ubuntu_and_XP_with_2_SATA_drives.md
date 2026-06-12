---
title: "Dual booting Ubuntu and XP with 2 SATA drives"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by GoogleyEyes on 2009-06-14
I have 2 drives, 1 for operating systems, the other for documents and files and I want to use the LiveCD option "Install them side by side, choosing between them each startup." However, this option only allows me to place it on /dev/sdb1 which is the wrong drive and gives me no options to change it. Other than specifying manually, are there workarounds?

---

### Post by hal8000 on 2009-06-14
You first need to make space if you want to Install Ubuntu.

The install program is choosing sdb1, this is the second SATA drive, first partition.

If you want to install on the other drive, sda, first shrink th XP partition using partition manager in XP or letting gparted do that for you, then install on the free space.

The boot loader, grub will let you choose which OS to boot, just make sure it installs on the mbr on hd0

---

### Post by presence1960 on 2009-06-14
Prior to shrinking the XP partition I would defrag windows at least once maybe twice. Windows throws files all over it's filesystem haphazardly. This will minimize the chance of data corruption/loss. This is of utmost importance. Do not skip this step. 

Back up all data you can not afford to lose. Even though partitioning & install operations are very smooth, there is always a chance of something going wrong- don't be the one caught with your pants down whining on here that you lost your data.

I would recommend using the gparted Live CD to create a new partition from your windows partition. Get it here : [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
The Ubuntu Live CD will do the job also. 

when ready to install use the manual option at the Prepare disk space window of the partitioner. choose your newly created partition for the install of Ubuntu.

---


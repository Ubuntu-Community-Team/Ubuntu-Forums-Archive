---
title: "Installed wrong ubuntu..."
date: 2008-07-23
forum: General Help
---

### Post by jefferyscotweir on 2008-07-23
Hey... I installed the wrong Ubuntu... I tried to install an Ubuntu 8.04 x86 when I should have installed a Ubuntu 8.04 AMD64. I would like to reinstall the correct version but when I try to delete the old Ubuntu partition using the CD it tells me that there is no root file directory found. Can anyone help me. Being the noob that I am? I suk! I uninstalled Ubuntu too somehow from my Windows Vista partition. I just went to an uninstall program and it uninstalled Ubuntu. So Ubuntu is gone but I need to reinstall the correct version on my other partition that I assigned for Ubuntu.

---

### Post by spupy on 2008-07-23
It sounds like you have trouble with selecting your partitions. When you install ubuntu, and you use the partitioner, you have to assign one of the partitions to be **root**(Enter "/" as mount path). Also, don't forget to create a swap partition. If the partitions from your last Ubuntu install are intact, you shouldn't have more problems with selecting the right partitions.

---

### Post by bodhi.zazen on 2008-07-23
You do not need to delete or remove the old in any way, just install the new over the top.

---

### Post by jefferyscotweir on 2008-07-24
Hey ... Thanks guys! I did exactly what you both said and it worked perfectly! I just set the partition that the old Ubuntu was on the ext3 format, set the mount to "/" and selected to format the partition. Replacing the old OS with the new version. Thanx!

---


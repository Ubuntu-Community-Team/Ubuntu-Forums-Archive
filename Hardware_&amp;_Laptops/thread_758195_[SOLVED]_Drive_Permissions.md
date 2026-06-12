---
title: "[SOLVED] Drive Permissions"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by yao_man on 2008-04-17
I initially installed ubuntu on my external hard drive using an Ubuntu 7.10 installation disk, but I have upgraded, reconfigured, and removed pieces to make my system currently run only Kubuntu 8.04. When I installed, I partitioned my drive to contaion a 4gb swap, a 10gb '/' partition, a 100 gb '/home' partition, and the rest of the 500gb drive went to a fourth fat32. At installation, I set the fourth drive (fat32) to mount at /external_disk, but now I want to change it to /media/external_disk. I also want to change the permissions to allow other users to read/write from/to that disk. I have read several forums about permissions etc. but don't really understand. How do I go about changing those two things? Thank you in advance for any help.

1) Change permissions to allow read/write for all users
2) Change mount point from /external_disk to /media/external_disk

---

### Post by Existentialist on 2008-04-18
2) You will want to edit your fstab:

sudo gedit /etc/fstab

You will see entries for all of the disks mounted at boot time.  The second block of text in each line is the mount point.  You should see it now as /external_disk, change this to /media/external_disk.

1) Take a look at this section of the Ubuntu article about adding a new hd.  You can modify permissions for multiple users, or groups. [https://help.ubuntu.com/community/InstallingANewHardDrive#head-fff5ec7d7c523059a4518c5db5bb68075cb46a43](https://help.ubuntu.com/community/InstallingANewHardDrive#head-fff5ec7d7c523059a4518c5db5bb68075cb46a43)

---

### Post by yao_man on 2008-04-18
Fantastic, thank you very much; that worked great. Everything is all fixed up now.

---


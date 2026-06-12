---
title: "dual boot with XP"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Nixforce on 2009-10-30
I current PC is running XP 64bit, and the HDD is partitioned 
[LIST]
[*]100GB NTFS XP 64 bit
[*]400GB NTFS Storage
[/LIST]

Im going to install Ubuntu 9.04 Server in the 1st partition. Is it possible to shrink the 100GB partition to install Ubuntu 9.04 Server so i can dual boot? I would prefer not to loose the XP until im 100% comfortable using alternatives for Dreamweaver, Photoshop. I have swapped a lot of my software to opensource alternates. All i need to be able to do develop my Web Apps in CFML and manage the MySQL, LDAP servers. 

Im lucky that there is a free CFML Server now (Openbluedragon).

---

### Post by mikewhatever on 2009-10-30
Well, you can't install on the first partition because it's occupied by Windows, but you can shrink it, thus making space for Ubuntu. Defragment and run disk check first.
On the other hand, [WUBI]("http://wubi-installer.org/") is a great way to skip the partitioning stage and install inside Windows.

---


---
title: "[SOLVED] Accessing partitions/other OSs in Xubuntu 8.1"
date: 2008-10-26
forum: General Help
---

### Post by utnubuuser on 2008-10-26
hello again --  Anybody know how to access other hdd/partions/disks in Xubuntu 8.10?

I just installed Xubuntu 8.10 to have a look-see (a triple boot  Ubuntu 8.04,  Ubuntu 8.10, and  Xubuntu 8.10), and during the install, the installer asks if you want to import settings etc from other partitions, but they don't show up on the desktop or in the file browser like they do in gnome.  Can they be reached through the terminal? And how?

Thanks

---

### Post by plucky on 2008-10-27
> **utnubuuser said:**
> hello again --  Anybody know how to access other hdd/partions/disks in Xubuntu 8.10?

I just installed Xubuntu 8.10 to have a look-see (a triple boot  Ubuntu 8.04,  Ubuntu 8.10, and  Xubuntu 8.10), and during the install, the installer asks if you want to import settings etc from other partitions, but they don't show up on the desktop or in the file browser like they do in gnome.  Can they be reached through the terminal? And how?

Thanks

In Xubuntu you will have to mount the partitions and add a line to **fstab** if you want them mounted for every boot.

See the Psychocats howto [Mount Linux Partitions](http://www.psychocats.net/ubuntu/mountlinux)


Good Luck

---

### Post by utnubuuser on 2008-10-27
Thanks Plucky

By chance, I discovered that the partitions also show up through Panel.

I was setting up a launcher in the top panel, and in the file browser that's accessed through the drop-down menus to configure the new icon, the partitions are listed.  They're not mounted, because you can't open them, but they are listed as Disk1, Disk2, Disk3, etc.

---


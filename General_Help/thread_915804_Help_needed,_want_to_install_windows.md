---
title: "Help needed, want to install windows"
date: 2008-09-10
forum: General Help
---

### Post by sameer.tahseen on 2008-09-10
Dear Friends: 

I installed ubuntu 8.04 on my system, but now i want to install windows as well, so that i could work on my projects that are saved with proprietary softwares and start my new projects with the open source softwares.

Plz it is urgent, i am a new migrant and your help is needed.

---

### Post by WRDN on 2008-09-10
If Ubuntu is using the entire HDD space, then you will need to resize the partitions. This can be done in GParted on the LiveCD. Resize the relevant partition, and format the unallocated space to NTFS or Fat32.
Now, run the Windows installation media, and at the relevant screen, select the NTFS/ Fat32 partition you just created. When it installs, Windows will overwrite GRUB with it's own MBR (Master Boot Record). This means you won't be able to boot Ubuntu until GRUB is restored- to restore if, follow [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") guide.
An alternative solution is to install Windows in a virtual machine so you don't need to resize/ create partitions, and the MBR will not be affected. I use [VirtualBox]("http://www.virtualbox.org/") personally.

---

### Post by mihaiv on 2008-09-10
Use gparted live cd to make some free space on your hard drive ([http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")).
After that simply install windows on that free space.

---

### Post by sameer.tahseen on 2008-09-10
Thanx Guys (Mihav and WRDN) it really helped. 
cheers

---


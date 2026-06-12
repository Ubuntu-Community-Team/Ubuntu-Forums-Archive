---
title: "installing ubuntu on USB Hard drive along with qemu"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by supershin on 2009-05-16
Basically I want to have a partition[~10GB] on the external hard drive to contain the OS Ubuntu. Another part of the partition will be shared space, formatted in FAT32 so windows and ubuntu can both access the files there[though not at the same time, heard it corrupts things]. And some other NTFS partitions for data.
I'm looking at two options :
1. Install ubuntu and qemu 
2. install coLinux.

Here are some tutorials from [http://www.pendrivelinux.com]("http://www.pendrivelinux.com")

1.
[http://www.pendrivelinux.com/colinux-portable-ubuntu-for-windows/](http://www.pendrivelinux.com/colinux-portable-ubuntu-for-windows/)
This one allows the latest ubuntu to be installed. To clarify something in step 5: Click install from the Ubuntu desktop and continue through the installation process. Proceed to install to hda -3.2GB Qemu Harddisk (the install will take some time "20-60 minutes")
If I partition the drive like how I wanted then I'll have to choose hda -10GB. Just want to make sure so i don't choose my internal drive.
Also will this work if I choose to install Kubuntu instead?


2.
This one uses CoLinux instead of qemu and "It just doesn't bother creating its own desktop, and puts all its windows inside your Windows, er, windows." and "It can work on, and save to, your Windows folders and files."
 It seems interesting enough though I'm not fond of the idea of interacting with windows like that because I'm thinking it can do some real damage if the virtual machine is compromised since it doesn't separate the OS'es like a regular dual-boot between Ubuntu and XP[NTFS]. I don't know much about this topic so can someone explain it.  

link to more info on coLinux portable Ubuntu:
[http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows)

So which is the better option? Any thoughts, experiences?

---


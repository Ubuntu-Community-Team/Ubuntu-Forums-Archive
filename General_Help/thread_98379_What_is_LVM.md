---
title: "What is LVM"
date: 2005-12-03
forum: General Help
---

### Post by Seminoles on 2005-12-03
I just installed  Breezy Badger 5.10 when it came time to partition the disk I selected erase entire disk use LVM something along that line can't remember exactly is this good since I no longer need windows? The only thing I can tell is I don't know how much free disk space I have when i run Disks under System/Administration/Disk it shows two hard drives the first on says Hard Disk 74.56 GiB the drive name and /dev/hda partition 1 /dev/hda 1 Extended 3 /boot 243.14 MiB (197) MiB Free Accessible, The other is Partition 5 /dev/hda 5 Unformatted Access Path none 74.32 (Free space not available) Inaccessible. The other hard disk is Unknown /dev/mapper/Ubuntu Partition ntu-root and Swap Partition. My question, is the partition 5 unformatted 74.32 GiB the Home where I need to put documents, pictures and other things that I would wont to back up and the root is where the file system is? If I have to reinstall Ubuntu because I mess things up will the partition 5 be cleaned or will it remain in tact?  :confused:

---

### Post by adam.skinner on 2005-12-03
[LVM2](http://www.tldp.org/HOWTO/LVM-HOWTO/) has it's own set of tools.  The [man pages]("http://www.linuxcommand.org/man_pages/lvm8.html") are a good place to start.

---


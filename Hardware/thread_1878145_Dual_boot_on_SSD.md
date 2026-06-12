---
title: "Dual boot on SSD"
date: 2011-11-09
forum: Hardware
---

### Post by Jimstehrman on 2011-11-09
hey all,

I'm looking to dual boot windows 7, Ubuntu and possibly another linux distro (ARCH or Fedora) from an mSATA SSD. 
Anyone have ideas as to what size SSD I should shoot for, and how much space I should allocate each partition? I have a good sized standard hard drive in my laptop already, so I have leg room for programs, just want to boot from the sata drive.

Thanks!

---

### Post by Matti L on 2011-11-09
10 GB is a good size for Ubuntu and many other Linux distros. Windows needs at least 50 GB I think and it's better to give it as much as there is free after one or two Linux partitions.

On a 100 GB SDD your partitioning could be like this:
Partition 1: 80 GB ntfs
Partition 2: 10 GB ext4
Partition 3: 10 GB ext4

And then put /home and swap on the second HD.

---

### Post by oldfred on 2011-11-09
Slight difference. /home has all your user settings and needs those loaded a lot, so keep /home inside root but put all data in the rotating drive.

You may want a lot of data in a shared NTFS partition. When I still used XP a lot I had Firefox & Thunderbird profiles & all photos in the NTFS partition. Then XP & Ubuntu had the same info. Now with little use for XP, most of my data goes into a ext3 /mnt/data partition with links to folders in /home. The data you use less often then is in the slower drive and all the system is in the faster SSD. I move any folder, including hidden folders that are just data into my data partitions. 

Arch recommends you use gpt for SSD's, but if dual booting with Windows you cannot do that unless booting in UEFI mode not BIOS.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---


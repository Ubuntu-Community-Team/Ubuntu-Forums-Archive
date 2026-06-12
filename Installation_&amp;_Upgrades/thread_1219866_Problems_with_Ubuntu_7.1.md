---
title: "Problems with Ubuntu 7.1"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Ant01 on 2009-07-22
I am having a lot of problems with Ubuntu 7.1 and am not sure if my system is corrupted and what I should do.

I first had problems with Rhythmbox so I uninstalled it but couldn't reinstall it, I continually get the error;
926225123365

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.11.2-0ubuntu4_i386.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.11.2-0ubuntu4_i386.deb)
  404 Not Found

I also tried to instal exaile but similar problem. My system also seems to have slowed down.

I have 148 updates available but when I try running the updates I get errors.

Please tell me what I should do?:confused:

---

### Post by Partyboi2 on 2009-07-22
Hi, 7.10 has reached its end of life and the repos moved, you would be better off upgrading to a later version.

---

### Post by Ant01 on 2009-07-22
> **Partyboi2 said:**
> Hi, 7.10 has reached its end of life and the repos moved, you would be better off upgrading to a later version.

Thanks

How do I upgrade to a later version, and which version should I use?

---

### Post by Ant01 on 2009-07-22
I found the upgrade in ubutu and its upgrading me to ver 8.04 I hope I am doing it the right way

---

### Post by Ant01 on 2009-07-22
The upgrade is not working if someone can please assist it says I don't have enough space, I should have more than enough space;:confused:

Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 774M free space on disk '/'. Please free at least an additional 598M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

root@antoine-ubuntu:/home/antoine# sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdc0fdc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3462    27808483+   7  HPFS/NTFS
/dev/sda2            3463        4799    10739452+  83  Linux
/dev/sda3            4800        4865      530145    5  Extended
/dev/sda5            4800        4865      530113+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x923b923b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        6375    51199155   83  Linux
/dev/sdb2            6376        9690    26627737+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059349504 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36f063ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

---

### Post by Partyboi2 on 2009-07-22
8.04 is a long term support version, so in my opinion  it's probably a better release to upgrade to as you wont have to upgrade for awhile if you don't want to.

Edit: Open a terminal and post the output to
```
 df -h
```

---

### Post by Ant01 on 2009-07-22
I did a search to download a fresh version and it takes me to version 9.04 should I rather download 9.04 and do a fresh installation. If so what do I do with the curnt version and the required space problem. I think I installed the curent version on the 40gig with windows but I dont use the windows anymore so I could clean that disc or install on the 80gig disc

---

### Post by Partyboi2 on 2009-07-23
If you want to install 9.04  and wipe windows off, you can backup your data you want to keep and wipe the hard drive clean and install 9.04 to the whole hard drive.
After you have backed up all the data you want to keep to another medium or to your 2nd hard drive, boot a ubuntu live cd and use gparted (System>Admin>Partition Editor) and delete all the partitions on the hard drive you want to use for Ubuntu, then run the installer and install Ubuntu using the whole hard drive.

---

### Post by starcannon on 2009-07-23
Backup important data, do a clean install to 8.04, be sure to make a separate /home partition if you have not already done so. 8.04 is a Long Term Support release, and is good for 3 years from its release date; generally its a great idea to just upgrade from LTS to LTS and skip the tweenleases. 

The release date is in the version number.

2008==8
April==04

GL and HF

---


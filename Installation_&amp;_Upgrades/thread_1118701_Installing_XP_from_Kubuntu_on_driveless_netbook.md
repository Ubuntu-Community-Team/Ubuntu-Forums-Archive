---
title: "Installing XP from Kubuntu on driveless netbook"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2009-04-07
Hi,
First I apologize raising the issue of installing a non-Linux OS in this forum. Since I've found a lot of knowledgeable people here, and since it will be a dual boot system, I'll post my question (please don't flame me).

I've just bought a nice netbook and successfully installed Kubuntu 9 beta on it without any problem! However, since my wife demands also XP, I plan to install also XP on that netbook. The problem is the netbook comes with NO CD/DVD drive. In order to prepare for a dual boot, I've manually partitioned the HD and intentionally left the first 2 primary partitions (sda1- 2 60GB NTFS, and sda2- a 10 GB FAT32) empty. My plan is to copy (in Linux) an XP CD (on another computer netted with the netbook), than reboot and use grub to point to sda2-hoping that the XP installation will start. Once I'll be done, I'll use sda2 to save an image of the fresh installed XP (using partimage). 

I would appreciate any tips regarding the above procedure or an alternative one.

Best Regards,

Michael Badt

---

### Post by Mark Phelps on 2009-04-07
I would be very surprised if that will work.  All that GRUB does, in the case of MS Windows OSs, is chain-load the MS Windows boot loader. You can point GRUB at any partition you want, but without an MS Windows boot loader present, it will not boot.

If you are able to copy the boot files from the WinXP CD to the root of the partition, it might work -- but I doubt it.

Also, realize that if it DOES work, XP will overwrite the MBR and GRUB, so after that, you will only be able to launch XP.  To get Ubuntu back, you will have to boot to a CD to restore GRUB.  How are you going to do that when your machine doesn't support booting to CD?

---

### Post by mibadt on 2009-04-07
Thanks Mark,
I'm aware that XP will over write my MBR, yet I can easily restore it by booting the Kubuntu live (from a USB-EASY in Linux) after installing XP.

Regards,

Michael Badt

---


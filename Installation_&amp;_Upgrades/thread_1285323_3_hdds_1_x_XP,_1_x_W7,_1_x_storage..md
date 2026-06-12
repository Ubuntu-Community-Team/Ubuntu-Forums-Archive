---
title: "3 hdds: 1 x XP, 1 x W7, 1 x storage."
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by frenchcr on 2009-10-07
sorry the title of this post should have read 1 x XP, 1 x ubuntu, 1 x storage --> want to add a 4th drive.



I have 2 x 250Gb drives, one with xp and the other with ubuntu, plus a 3rd drive which is 1Tb which keeps all my precious music and movies etc.

Im getting a Windows 7 Ultimate disk tommorow gratis of microsoft and want to add a 4th drive to install it on.

At the moment when i boot up, i get grub and can choose between xp and ubuntu...i want to be able to choose from these two AND windows 7.


[COLOR="DarkSlateBlue"]**How do i go about this i.e. i dont want to harm any of the 3 other drives?**[/COLOR]

---

### Post by frenchcr on 2009-10-08
do I need to unplug some of the drives, or all of them? i'm not sure how to begin.

---

### Post by frenchcr on 2009-10-08
bump

---

### Post by louieb on 2009-10-08
Should be safe enough. But windows has a weird way of dual booting when its installer finds another windows  install.  May want to unplug the drive with XP on it. [Multibooters, Pictures here worth 1000 words]("http://www.multibooters.co.uk/multiboot.html")

---

### Post by Mark Phelps on 2009-10-10
MS windows has a tradition of install the boot loader into the first MS-windows-formatted drive it finds.

The problem you will have when you install Windows 7 to a new drive is that, by default, it will install two partitions -- a BOOT partition and a regular NTFS partition.  If it then installs the boot loader files into the BOOT partition, you should be OK.  But if it installs the boot loader files into the XP partition, it's then possible that Windows 7 will not then boot.

I would recommend that you disconnect the XP drive when you install Windows 7.  That will at least ensure that you have a bootable Windows 7 when done.  You will then have to modify menu.lst manually to add a stanza for Windows 7.

---


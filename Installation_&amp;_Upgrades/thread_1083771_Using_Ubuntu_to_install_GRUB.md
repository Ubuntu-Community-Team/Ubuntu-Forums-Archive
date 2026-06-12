---
title: "Using Ubuntu to install GRUB"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by mpn_1990 on 2009-03-01
I have an old PC that I would like to dual-boot Windows 2000 and Windows 98. Windows 2000 is already installed on one big partition. I plan on shrinking this with gparted by 2GB for the one that will hold Windows 98.

Now here's my question. I want to use the Ubuntu Live CD to install GRUB so that I have a boot menu to choose between the two. How would I do this, and in what order? I think installing Windows 98 onto the second partition after 2000 is going to overwrite the MBR so that the PC automatically boots into 98 as if 2000 didn't exist. So would I resize the partition, install 98, then install GRUB? The Windows 2000 partition is FAT32, so 98 would see it.

---

### Post by thtrgremlin on 2009-03-01
If you do not want ubuntu installed on the machine, then you will need a /boot partition to hold all of your information, but personally, if not using Gnu/Linux on the computer, just use the Windows Boot loader and edit the entries in boot.ini.

However, an ubuntu Live CD would be your best bet for resizing and creating a new partition for Windows 98.

I will mention however that with Wine v1.0, Gnu/Linux has full support for (near) all Windows 98 applications. Add DosBox to that and you can run everything earlier. What are you hoping to do with 98 that you can't do in 2000?

---

### Post by caljohnsmith on 2009-03-01
Instead of making a dedicated Grub partition to boot both your Windows OSes, you could use "[Grub4DOS]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip")" inside one of your Windows partitions. Also, you can download the "[grub_install.exe]("http://download.gna.org/grubutil/grubinst-1.1-bin-w32-2008-01-01.zip")" GUI app to make installing Grub4DOS to the MBR really easy. Let me know how that goes or if you need more specific directions for using Grub4DOS.

---

### Post by thtrgremlin on 2009-03-01
Never heard of grub4dos. Just from here, thank you!

---


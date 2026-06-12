---
title: "Avoid GRUB in MBR when installing, how to?"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by arnoldus on 2009-06-12
I want to install Ubuntu on my netbook, but don't want GRUB as the bootloader in the MBR, I want to keep the NTLDR and then chainload GRUB or GRUB4DOS from NTLDR.
Several sites mention to do a normal install, then FIXBOOT from Windows recovery to restore the windows MBR, and then chainload Grub from Ntldr (modify boot.ini). This is not possible from my netbook as I don't have a cd-rom or a windows cd, and additionally I don't feel comfortable overwriting the MBR in this way.

How do I proceed?

---

### Post by dstew on 2009-06-12
At step 7 in the install process, the "Ready to Install" page, there is an Advanced button at the bottom. Click there, and I think you have the option to **not** install a boot loader. Configuring dual boot with the Windows boot system will then be left for you to do at your leisure. You might want to install grub into the **boot sector** of the Ubuntu partition (choice of (hd0,1) or something like that) so that Windows can chainload Ubuntu.

---

### Post by arnoldus on 2009-06-12
Thank you, seems manageable.
Is it trial-and-error which number I put in the hd(0,x) or is there a method of finding it out with a command?

---

### Post by dstew on 2009-06-12
During the installation, you have to designate a root partition (mount point '/', without the single quotes). Install grub to that partition. If for some reason you create a separate /boot partition, then I would install grub to that one. Just remember the partition designation from the partitioning step.

The *partition* notation for grub is (hd0,0) for /dev/sda1, (hd1,0) for /dev/sdb1, (hd1,1) for /dev/sdb2 etc. Instead of sda or sdb, the notation for *disks* (to install in MBR) is (hd0) or (hd1).

---


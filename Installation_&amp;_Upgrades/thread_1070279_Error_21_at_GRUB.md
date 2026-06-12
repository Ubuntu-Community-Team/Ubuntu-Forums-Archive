---
title: "Error 21 at GRUB"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by appledoze on 2009-02-15
I just installed a dual boot Ubuntu. But everytime I start the computer and accesses grub to select the OS it tells me error 21. I installed Ubuntu in a partition on a external hard drive, and I checked that all my Windows files are still in the internal one. And I can still access BIOS too. What do I do?

---

### Post by sahabcse on 2009-02-15
Mount the External hard disk and fix the grub. For fixing the grub follow

==============================================
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
==============================================

Regards
Sahab

---

### Post by appledoze on 2009-02-15
That's the problem, I can't mount the external HDD from BIOS because it doesn't even read it no matter what. It's a USB drive, so maybe that explains why. As for the GRUB reinstallation method, I'm about to try it.

Also, what I noticed is that when I partitioned free space in my external drive for Ubuntu, it accidentally came with a strange file that I can't do crap with, not even delete, because it says I don't have permission to.

---

### Post by appledoze on 2009-02-15
I was able to get the USB hard drive to be detected at the boot priority selection in BIOS, and I set it at the top of the priority list. Now it gives me error 17! And I still can't set its type or mode.

I went into the live CD demo, accessed the terminal, and typed in sudo fdisk -l. I discovered that there was a small partition in the internal drive that accidentally had some linux data, when it was supposed to be in the external one. I deleted that partition, but  still got error 17 after rebooting

---

### Post by appledoze on 2009-02-16
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x45704570

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78140159    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   287563499   143781718+   c  W95 FAT32 (LBA)
/dev/sdb2       287563500   312576704    12506602+   b  W95 FAT32
ubuntu@ubuntu:~$ 

I think the problem may be that /dev/sdb1 is set at LBA, when it should be auto. How do I change this at BIOS?

---

### Post by caljohnsmith on 2009-02-16
Both the drives you show have only NTFS/FAT partitions on them; where did you install Ubuntu to? Ubuntu needs a linux file system like ext3 in order to work. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Live Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---


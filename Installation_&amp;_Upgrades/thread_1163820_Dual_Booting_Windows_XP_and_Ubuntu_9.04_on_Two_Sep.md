---
title: "Dual Booting Windows XP and Ubuntu 9.04 on Two Separate Disks"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by mfergus3 on 2009-05-19
Hi all, this should be a relatively simple issue to solve for someone who's good with GRUB/Booting issues.  I have two SATA hard drives.  I installed Windows XP on one of the drives, then did a clean install of Ubuntu on the other.  I added Windows XP to GRUB with "root (hd1)".  When I start up, I can see the Windows XP entry in the GRUB menu just fine, but when I try to boot it I get:

BOOTMGR is missing
Press Ctrl+Alt+Del to restart

So I'm assuming my re-install of Ubuntu over-wrote the MBR on the Windows XP disk.  Is there an easy way to re-install the MBR?  I tried installing lilo and using that to install/re-install a MBR on the Windows XP drive but it didn't appear to make any difference.  Any other issues that could be causing this that I'm not realizing?  This is on two seperate disks, I'm surprised Ubuntu would have caused an issue with the MBR on the Windows XP drive.  Am I understanding this wrong?

---

### Post by mfergus3 on 2009-05-19
Here's fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bbb9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      181270  1456051243+  83  Linux
/dev/sda2          181271      182401     9084757+   5  Extended
/dev/sda5          181271      182401     9084726   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS



And /boot/grub/menu.lst:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f67f7a8f-99b8-4979-8276-4ff9059d5160
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f67f7a8f-99b8-4979-8276-4ff9059d5160 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f67f7a8f-99b8-4979-8276-4ff9059d5160
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f67f7a8f-99b8-4979-8276-4ff9059d5160 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
uuid		f67f7a8f-99b8-4979-8276-4ff9059d5160
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f67f7a8f-99b8-4979-8276-4ff9059d5160 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid		f67f7a8f-99b8-4979-8276-4ff9059d5160
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f67f7a8f-99b8-4979-8276-4ff9059d5160 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
uuid		f67f7a8f-99b8-4979-8276-4ff9059d5160
kernel		/boot/memtest86+.bin
quiet

title		Windows 95/98/NT/2000
root		(hd1,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST



And /boot/grub/device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by finito on 2009-05-19
Try reading this post.

[http://ubuntuforums.org/showthread.php?t=1163503](http://ubuntuforums.org/showthread.php?t=1163503)

What is easy is just fix the MBR via Windows boot disk and then try the setup mentioned for windows.

---


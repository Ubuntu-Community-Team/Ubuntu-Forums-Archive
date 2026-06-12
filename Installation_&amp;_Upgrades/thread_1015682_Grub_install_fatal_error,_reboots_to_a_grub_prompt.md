---
title: "Grub install fatal error, reboots to a grub prompt"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by PeterRJG on 2008-12-19
I have a 500 Gb SATA drive, 400GB of which is Windows XP and the rest set aside for Linux. I had Fedora 10 on it before and it booted using its version of Grub. I got rid of Fedora and installed Xubuntu 7.10 from a live CD and it got to 94% before it bombedhttp://www.linux-tip.net/cms/content/view/354/27/ out with a grub fatal error. Upon reboot it goes straight to a grub prompt, and I have no idea what to do next.

I've googled, but I'm getting confusing and conflicting answers.

Thanks in advance.

---

### Post by PeterRJG on 2008-12-19
Here's the output of the boot_info txt file:

/dev/sda:Grub:0000
sda1 :ntfs:BS: XP:OS : /boot.ini /ntldr /NTDETECT.COM 
sda2 :swap:BS: None:OS : 
sda3 :ext3:BS: None:OS Linux: /boot /boot/grub 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x61fdff12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   819200062   409600000    7  HPFS/NTFS
/dev/sda2       819202545   819604169      200812+  82  Linux swap / Solaris
/dev/sda3       819604170   976768064    78581947+  8e  Linux LVM
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=819200000, Id= 7, bootable
/dev/sda2 : start=819202545, size=   401625, Id=82
/dev/sda3 : start=819604170, size=157163895, Id=8e
/dev/sda4 : start=        0, size=        0, Id= 0

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


sda3/boot

total 17484
drwxr-xr-x  3 root root    4096 2008-12-19 17:43 .
drwxr-xr-x 21 root root    4096 2008-12-19 17:43 ..
-rw-r--r--  1 root root  424317 2007-10-15 01:39 abi-2.6.22-14-generic
-rw-r--r--  1 root root   75311 2007-10-15 01:39 config-2.6.22-14-generic
drwxr-xr-x  2 root root    4096 2008-12-19 17:43 grub
-rw-r--r--  1 root root 7517802 2008-12-19 17:43 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 7122208 2007-10-16 00:58 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  823535 2007-10-15 01:39 System.map-2.6.22-14-generic
-rw-r--r--  1 root root 1764280 2007-10-15 01:39 vmlinuz-2.6.22-14-generic

sda3/boot/grub

total 200
drwxr-xr-x 2 root root   4096 2008-12-19 17:43 .
drwxr-xr-x 3 root root   4096 2008-12-19 17:43 ..
-rw-r--r-- 1 root root    197 2008-12-19 17:43 default
-rw-r--r-- 1 root root     15 2008-12-19 17:43 device.map
-rw-r--r-- 1 root root   8660 2008-12-19 17:43 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2008-12-19 17:43 fat_stage1_5
-rw-r--r-- 1 root root   9152 2008-12-19 17:43 jfs_stage1_5
-rw-r--r-- 1 root root   7860 2008-12-19 17:43 minix_stage1_5
-rw-r--r-- 1 root root  10132 2008-12-19 17:43 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-19 17:43 stage1
-rw-r--r-- 1 root root 110292 2008-12-19 17:43 stage2
-rw-r--r-- 1 root root   9980 2008-12-19 17:43 xfs_stage1_5

---

### Post by caljohnsmith on 2008-12-19
Unfortunately that fatal Grub install error at 94% is a known bug. One way that many users have been able to workaround it though is to click the "advanced" button near the end of the installation process and specify to have Grub installed to /dev/sda (in your case). How about giving that a shot and let me know if it works, and if it doesn't, I know of at least one other workaround you can try.

---


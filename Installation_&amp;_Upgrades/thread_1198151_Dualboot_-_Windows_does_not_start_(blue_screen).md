---
title: "Dualboot - Windows does not start (blue screen)"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by linuxfriendly on 2009-06-27
Hello All,

1. I did a dual boot install with ubuntu 9.04. 
2. Now Windows does not start with the blue screen  0x0000007B (0xF789E63C, ...., is a very common problem as I found on the internet BUT
3. my windows installation is on the master drive I: Windows chose this when I installed last time, so I left it. My slave drive is c:, I know that cries for trouble
4. I went and installed ubuntu 9.04
5. I chose sdb because the ubuntu installer saw the windows OS there
6. The comand  
> sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13541354

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38587   309950046    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeafa6f04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdb2           16709       24321    61151422+   5  Extended
/dev/sdb5           16709       24005    58613121   83  Linux
/dev/sdb6           24006       24321     2538238+  82  Linux swap / Solaris
7. The menu.lst shows
> title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2f62140d-806d-4829-8c01-4c4d168443cf
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2f62140d-806d-4829-8c01-4c4d168443cf ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2f62140d-806d-4829-8c01-4c4d168443cf
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2f62140d-806d-4829-8c01-4c4d168443cf ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2f62140d-806d-4829-8c01-4c4d168443cf
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
I know this is a problem to tell windows properly where it is and/or BIOS settings playing a role, too. I had to change the boot priority in my BIOS to get into the grub menu. Otherwise windows tried to boot immediatly into the blue screen.

I still hope, I can  run Windows but am willing to install it again so it lands on C: this time which will help when reinstalling ubuntu afterwards. But perhaps you can help me to get it going with the little bit weird configuration.

Thanks in advance
Peter

---

### Post by Hobgoblin on 2009-06-27
> **linuxfriendly said:**
> 
3. my windows installation is on the master drive I: Windows chose this when I installed last time, so I left it. My slave drive is c:, I know that cries for trouble


Cries for trouble with Windows but drive letters don't mean anything to Linux.

I'm guessing the resize of the partition went wrong.  So, just reinstall Windows and restore your data from your latest backup.

---

### Post by stubrownuk on 2009-06-27
Are you able to download, or do you already have, SystemRescue CD? If all else fails, at least that enables you to recover your data from unbootable partitions if you don't ready have it backed up elsewhere, and it may also help in diagnosing and fixing the problem. For dual booting, I find it's less hassle to start with Windows and then install Jaunty alongside it, rather than the other way round. I've tried all permutations, but I keep coming back to that as the only really reliable way of doing it.

---

### Post by presence1960 on 2009-06-27
> **stubrownuk said:**
> Are you able to download, or do you already have, SystemRescue CD? If all else fails, at least that enables you to recover your data from unbootable partitions if you don't ready have it backed up elsewhere, and it may also help in diagnosing and fixing the problem. For dual booting, I find it's less hassle to start with Windows and then install Jaunty alongside it, rather than the other way round. I've tried all permutations, but I keep coming back to that as the only really reliable way of doing it.

it is not hard to install windows after Ubuntu, don't feed that myth. Use either Partition Editor from Ubuntu Live CD (System > Administration > Partition Editor) or gparted Live CD to get your partitions in order. If you decide to reinstall windows go into BIOS and set the disk you are going to put windows onto as first boot in the hard disk boot order. Then pop in the install CD and install windows to that disk. When done go back into BIOS and switch the order back so the disk with Ubuntu boots before the windows disk. Boot your machine and GRUB should come up. You may have to edit menu.lst to get your windows entry to boot. But we'll cross that bridge when you get there.

---

### Post by irv on 2009-06-27
The quick and easy fix is to just put the XP CD in the drive and boot from it. Run the second fix. What I mean by this this is when the first menu comes up there is a fix on it, don't chose that one. Wait until you see the next menu that says fix. This one will re-install Windows but it will not change or delete your files or programs you already have installed on it. After this is done, just remove the CD and boot normally.

---

### Post by linuxfriendly on 2009-06-27
Thanks for all the answers. I thought there could be a configuration in the grub menu to let Windows start but I guess the partitioning went wrong. I admit that this windows box was already hardware wise not quite in order. I have to check the master slave issue etc. as windows went on the &quot;wrong&quot; drive in the last install :D.
However it is only my game box as I use another computer with linux for the real world. I will reinstall Windows and Ubuntu and have a backup of my data done.

Thanks again


Peter 

 Update: Reinstalled Winsuck and it was indeed a partitioning problem.
Thanks for your help here.

 Peter

---


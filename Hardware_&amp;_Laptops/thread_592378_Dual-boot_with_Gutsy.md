---
title: "Dual-boot with Gutsy???"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by mariner09 on 2007-10-26
Has anyone seen or put together a good dual-boot XP/Gutsy install how-to?

My machine came with windows and I don't want to lose that partition.  I know I should shrink the existing partition and maybe make a fat32 partition for file sharing and then use the rest for linux.

Any pointers would greatly be appreciated...

---

### Post by powermaster on 2007-10-31
Do a backup before you try this just in case. I'm doing dual boot with WinXP Pro 32bit with Gutsy 64bit, using grub as bootloader

1. You could use gpart to resize your partition. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

My partition as shown

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10448    83923528+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           10449       19080    69336540   83  Linux
/dev/hda3           19081       19453     2996122+  82  Linux swap / Solaris

2. Boot up gutsy from CD, double click on the Install and follow the following steps.
[LIST=1]
[*]Select Language and click Forward
[*]Select Country / Timezone and click Forward
[*]Select Keyboard Layout and click Forward
[*]Select Manual and click Forward
[*]Create one root partition and one swap partition. I experienced some peculiar problems with windows when doing chkdsk last time. so normally I leave some unused space about 8mb to 32mb. so far so good.
[*]Migrate Documents and Settings and click Forward
[*]Enter login details/ password and click Forward
[*]Click on Advanced make sure Install boot loader is tick, device for boot loader installation is (hd0) and click ok
[*]Click Install to start the installation
[/LIST]

My /boot/grub/menu.lst looks as follows
__________________________________________________________________
default		4
timeout		10

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5e9c1cf7-2546-4def-8034-15a504b6cd90 ro
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5e9c1cf7-2546-4def-8034-15a504b6cd90 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
_______________________________________________________________________

For the file sharing, I'm using ntfs-3g to write to ntfs partition. So far so good too.

---

### Post by louieb on 2007-10-31
Two very good sites
Live CD install [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")
Alternate CD install [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---


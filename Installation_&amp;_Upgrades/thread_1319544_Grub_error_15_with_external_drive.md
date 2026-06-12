---
title: "Grub error 15 with external drive"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by alcidespinto on 2009-11-08
I'm a newbie, so please try avoid hard technical stuff.
 
I recently installed Xubuntu in my USB external HD, keeping WinXP in my laptop internal HD. However, when I try to boot from the USB, I get Grub error 15.
 
Here is some revelant data:
 
[FONT=Book Antiqua]Disk /dev/sda: 60.0 GB, 60011642880 bytes[/FONT]
[FONT=Book Antiqua]255 heads, 63 sectors/track, 7296 cylinders[/FONT]
[FONT=Book Antiqua]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
[FONT=Book Antiqua]Disk identifier: 0xd744d744[/FONT]
 
[FONT=Book Antiqua]Device Boot Start End Blocks Id System[/FONT]
[FONT=Book Antiqua]/dev/sda1 * 1 6020 48355618+ 7 HPFS/NTFS[/FONT]
[FONT=Book Antiqua]/dev/sda2 6021 7295 10241437+ f W95 Ext'd (LBA)[/FONT]
[FONT=Book Antiqua]/dev/sda5 6021 7295 10241406 7 HPFS/NTFS[/FONT]
 
[FONT=Book Antiqua]Disk /dev/sdb: 500.1 GB, 500107862016 bytes[/FONT]
[FONT=Book Antiqua]255 heads, 63 sectors/track, 60801 cylinders[/FONT]
[FONT=Book Antiqua]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
[FONT=Book Antiqua]Disk identifier: 0x0c4b9758[/FONT]
 
[FONT=Book Antiqua]Device Boot Start End Blocks Id System[/FONT]
[FONT=Book Antiqua]/dev/sdb1 * 1 57477 461683971 7 HPFS/NTFS[/FONT]
[FONT=Book Antiqua]/dev/sdb2 57478 60801 26700030 5 Extended[/FONT]
[FONT=Book Antiqua]/dev/sdb5 57478 57732 2048256 82 Linux swap / Solaris[/FONT]
[FONT=Book Antiqua]/dev/sdb6 57733 60801 24651711 83 Linux[/FONT]
 
File menu.lst (part of the file):
 
[FONT=Arial][FONT=Book Antiqua]title Ubuntu 9.04, kernel 2.6.28-11-generic[/FONT]
[FONT=Arial]uuid d444a31c-966f-44bf-834c-9e665f83187a[/FONT]
[FONT=Arial]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d444a31c-966f-44bf-834c-9e665f83187a ro quiet splash [/FONT]
[FONT=Arial]initrd /boot/initrd.img-2.6.28-11-generic[/FONT]
[FONT=Arial]quiet[/FONT]
 
[FONT=Arial]title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/FONT]
[FONT=Arial]uuid d444a31c-966f-44bf-834c-9e665f83187a[/FONT]
[FONT=Arial]kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d444a31c-966f-44bf-834c-9e665f83187a ro single[/FONT]
[FONT=Arial]initrd /boot/initrd.img-2.6.28-11-generic[/FONT]
 
[FONT=Arial]title Ubuntu 9.04, memtest86+[/FONT]
[FONT=Arial]uuid d444a31c-966f-44bf-834c-9e665f83187a[/FONT]
[FONT=Arial]kernel /boot/memtest86+.bin[/FONT]
[FONT=Arial]quiet[/FONT] 
[/FONT]
File fstab:
 
[FONT=Arial][FONT=Book Antiqua]# /etc/fstab: static file system information.[/FONT]
[FONT=Arial]#[/FONT]
[FONT=Arial]# Use 'vol_id --uuid' to print the universally unique identifier for a[/FONT]
[FONT=Arial]# device; this may be used with UUID= as a more robust way to name devices[/FONT]
[FONT=Arial]# that works even if disks are added and removed. See fstab(5).[/FONT]
[FONT=Arial]#[/FONT]
[FONT=Arial]# <file system> <mount point> <type> <options> <dump> <pass>[/FONT]
[FONT=Arial]proc /proc proc defaults 0 0[/FONT]
[FONT=Arial]# / was on /dev/sdb6 during installation[/FONT]
[FONT=Arial]UUID=d444a31c-966f-44bf-834c-9e665f83187a / ext3 relatime,errors=remount-ro 0 1[/FONT]
[FONT=Arial]# swap was on /dev/sdb5 during installation[/FONT]
[FONT=Arial]UUID=01a1fdd4-6921-4ced-9243-e72735225d6e none swap sw 0 0[/FONT]
[FONT=Arial]/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0[/FONT]
[/FONT]
I read many posts and tried many solutions, but until now none solved my problem.
Please help me. I want to use Ubuntu.

---


---
title: "Windows hates Grub-- won't let me back in"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by tmoneygetpaid on 2009-04-17
Thank you for reading.

I can't get into my Windows installation. I've been having problems with grub-- somehow after the last ubuntu updates it was pointing to the incorrect partition to start windows, which I changed back and got into win. But now I get to a screen asking me to boot into safe mode, safe mode with networking, etc., etc. After I make a choice I see the white ascii bar on the bottom fill up and instantly the system restarts, just before I'd get the login screen.

I've tried pointing to all the partitions on both disks of my system, I've tried doing the map one drive to the other (map hd1 hd0/ map hd0 hd1), and then it complains that NTLDR is missing. I'm boggled here.

Here's the win entry for GRUB:

rootnoverify (hd1,0)
chainloader +1
savedefault
makeactive

fdisk -l says:
cannot open /dev/sda
cannot open /dec/sdb

I've done some stuff to make sure it wasn't the disk (full long test in seatools from the UBCD) or windows config (tried last known good config; tried do not restart on system error) to no avail. I remember this happening on a system I setup at work to dual boot, but I think the remap solved it there.

Please help!

---

### Post by Herman on 2009-04-17
> I can't get into my Windows installation. I've been having problems with grub-- somehow after the last ubuntu updates it was pointing to the incorrect partition to start windows, which I changed back and got into win. But now I get to a screen asking me to boot into safe mode, safe mode with networking, etc., etc. After I make a choice I see the white ascii bar on the bottom fill up and instantly the system restarts, just before I'd get the login screen.If you have the Windows screen asking if you want to boot into 'safe mode' or 'normal boot' and so on, you are already in Windows, or at least you're in the Windows boot loader and GRUB has already done it's job of chainloading Windows. Most likely, your problem has nothing to do with Ubuntu or GRUB, but you have a Windows problem.

Sometimes Windows problems are easy to fix and sometimes they can take days and be extremely complicated. I would begin by booting your Windows XP 'Installation CD', open a  [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run CHKDSK /F or CHKDSK /R.

If your Windows still won't boot after that, it could have any problem from third party software compatibilty problems to viruses and so on. Who knows?

It might still be interesting to see your fdisk output anyway,
```
sudo fdisk -lu
```and at least the bottom half of your /boot/grub/menu.lst too if you like,
```
gksudo gedit /boot/grub/menu.lst
```Regards, Herman :)

---

### Post by tmoneygetpaid on 2009-04-17
You're surely right-- I let windows install its own bootloader to the MBR and tried to boot and, still, no dice. So it's something there.

Going to post these anyway. And I'm going to boot into the recovery console right now and run those commands.

Thanks a lot.

fdisk:
[quote="fdisk"]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004b8cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   327677804   163838871    7  HPFS/NTFS
/dev/sda2       327677805   587320334   129821265    7  HPFS/NTFS
/dev/sda3       971241705   976768064     2763180    5  Extended
/dev/sda4       893117610   971241704    39062047+  83  Linux
/dev/sda5       971241768   976768064     2763148+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003b39a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   245762369   122881153+   7  HPFS/NTFS
/dev/sdb2       2457
[/quote]

menu.lst:
[quote="menu.lst"]
title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=d3c63bdf-94b0-4e8b-84f3-eea41ce73525 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
chainloader +1
savedefault
makeactive

[/quote]

---

### Post by tmoneygetpaid on 2009-04-17
chkdsk /r didn't solve this.

going to try a malicious software scan.

---


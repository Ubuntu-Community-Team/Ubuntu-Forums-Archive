---
title: "Dual boot IDE and SATA hdd"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by Big-Wayne on 2007-01-29
Hi,
I have two questions;

**1.** I have just upgraded my drive to SATA and installed Edgy on it, I put the old 40gb IDE drive back in and installed Windows XP on it. I followed the instructions here [http://www.ubuntuforums.org/showthread.php?t=275728]("http://www.ubuntuforums.org/showthread.php?t=275728") for adding the XP drive to show in grub list but when I choose it I get (error:Unrecognised device string)
Grub list; 
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

title		Windows XP MCE
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
makeactive
chainloader	+1
### END DEBIAN AUTOMAGIC KERNELS LIST

**2.**How do I enter the info on fstab so I can mount my Windows Drive (IDE) when I boot into linux on the SATA hdd. I tried mounting from shell and it said there was no entry in fstab.
fdisk -l gives me;

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30119   241930836   83  Linux
/dev/sda2           30120       30401     2265165    5  Extended
/dev/sda5           30120       30401     2265133+  82  Linux swap / Solaris

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

---

### Post by Big-Wayne on 2007-02-05
Fixed it using info from the ubuntuguide wiki;
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")
:) :)

---


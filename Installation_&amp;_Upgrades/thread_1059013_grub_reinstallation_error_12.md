---
title: "grub reinstallation error 12"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by pigcat on 2009-02-03
hi I am trying to reinstall grub after windows xp wiped it out following the instructions from:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I get :

"Error 12: Invalid device requested"

after the command: 

"setup (hd0)"

I try deleting windows xp on my primary partition to see if it would boot into my ubuntu(partition 2) but it just hangs there so im running ubuntu from the livecd.

output for: sudo fdisk -l 

omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd92cbe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16356   131379538+   7  HPFS/NTFS
/dev/sda2           16357       38913   181189102+   5  Extended
/dev/sda3           37994       38913     7389868+  82  Linux swap / Solaris
/dev/sda5           16357       37110   166706442   83  Linux
/dev/sda6           37111       37993     7092666   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006da0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    7  HPFS/NTFS




and I get "cat: /boot/grub/menu.lst: No such file or directory" 

for "cat /boot/grub/menu.lst"

any help would be greatly appreciated!

---

### Post by dstew on 2009-02-03
It may be that the MBR of (hd0) is not accessible for some reason. It is possible that the BIOS is protecting it. You might check for security settings in BIOS. Some BIOses will have settings that prevent the MBR from being written to try to avoid certain kinds of viruses. Since you are not trying to access a partition with the setup command, I don't think the usual tricks like setting partition boot flags with GParted will help.

When you did "find /boot/grub/menu.lst" did it return (hd0,4)? If so, you might need to do "root (hd0,4)" before you try "cat /boot/grub/menu.lst", or try ```
cat (hd0,4)/boot/grub/menu.lst
```

I assume you are running grub from a Live CD boot.

---


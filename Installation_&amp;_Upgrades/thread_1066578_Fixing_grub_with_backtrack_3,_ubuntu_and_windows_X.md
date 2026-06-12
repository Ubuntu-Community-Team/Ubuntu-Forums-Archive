---
title: "Fixing grub with backtrack 3, ubuntu and windows XP"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by maimed on 2009-02-11
hey i have a big problem. I recently installed bracktrack 3 on my pc with ubuntu and windows xp, got grub working normal goes to XP and ubuntu fine but it can't find backtrack 3 (yes i did installed in, via an installer i did a real installion to a seperate partition) 
I have no idea what to type into grub to get it working and i have no idea what the partition number is.
Here is fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a695750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10        1315    10485760    7  HPFS/NTFS
/dev/sda3            1316       17730   131853487+   f  W95 Ext'd (LBA)
/dev/sda4           17731       30401   101779807+  83  Linux
/dev/sda5            1316        7750    51689106    7  HPFS/NTFS
/dev/sda6            7751       10944    25655773+  83  Linux
```

I am pretty sure it is on that sda6 one. sda5 is windows and sda4 is ubuntu. 1 and 2 are recovery etc that came with laptop.
Here is grub menu.lst

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		881c39ab-8a33-45cb-8e12-c8a515056635
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=881c39ab-8a33-45cb-8e12-c8a515056635 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		881c39ab-8a33-45cb-8e12-c8a515056635
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=881c39ab-8a33-45cb-8e12-c8a515056635 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic


title		Ubuntu 8.10, memtest86+
uuid		881c39ab-8a33-45cb-8e12-c8a515056635
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1



```

So how do i add it in so i can get to backtrack via grub.
Thankyou

---

### Post by maimed on 2009-02-11
is there anyway to tell what o/s is installed on what partiton?

---

### Post by Binerial on 2011-04-07
I would try going into Ubuntu and opening up the terminal, type in **sudo update-grub**  or **sudo update-grub2**. This should get the bootloader to bring up Backtrack correctly.

---


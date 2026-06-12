---
title: "Yet another NTLDR is missing"
date: 2008-09-04
forum: General Help
---

### Post by jijin on 2008-09-04
Ok... this is a normal "NTLDR is missing" thread, and I know enough in Linux to get me in trouble so I'm asking for help :D

/boot/grub/menu.lst :

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce435f8e-22b9-4d50-857a-f98ea15ba7f7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce435f8e-22b9-4d50-857a-f98ea15ba7f7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows NT/2000/XP
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```


output of sudo fdisk -l

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcee7719

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23565   189285831   83  Linux
/dev/sda2           23566       24321     6072570    5  Extended
/dev/sda5           23566       24321     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x724a724a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000689ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

```

I have three disks.. one 200g for ubuntu its ext3, one 250g for winxp it's NTFS, and one 200g for all my junk which is NTFS.

All drives are mountable and usable in ubuntu, and I can see the ntldr file on the winxp install.

Thanks for the help in advance.

---

### Post by caljohnsmith on 2008-09-04
Your problem might be as simple as Grub not looking for Windows on the correct disk; unfortunately Grub can see the order of HDDs different than the way BIOS orders them. So, first try the following in your menu.lst and see if it works:
```
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by jijin on 2008-09-04
> **caljohnsmith said:**
> Your problem might be as simple as Grub not looking for Windows on the correct disk; unfortunately Grub can see the order of HDDs different than the way BIOS orders them. So, first try the following in your menu.lst and see if it works:
```
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```


That fixed it. Thanks

---


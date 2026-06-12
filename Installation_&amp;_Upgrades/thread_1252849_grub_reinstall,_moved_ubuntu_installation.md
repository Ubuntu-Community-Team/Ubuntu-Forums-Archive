---
title: "grub reinstall, moved ubuntu installation"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by metalfan_ on 2009-08-29
Hi,

since i had problems with grub in the past i would like to ask this time if what im planning todo should work.

Ive installed ubuntu to my internal sata drive, after that i installed another ubuntu version to my external usb drive. the second ubuntu installation is currently running.

if i detach the usb drive and boot i get some grub error, which indicates that grub is installed on sda but uses /boot/grub from my external harddrive...yes?

The target is to copy the ubuntu from my external drive to the internal.

the internal ubuntu resides on /dev/sda6, i did rsync my current installation to /dev/sda7.

now to get grub reading its files from /dev/sda7 i would do the following:


```

mount /dev/sda7 /mnt/newsys
chroot /mnt/newsys
grub-install /dev/sda

```


```

#the first entry from /boot/grub on /dev/sda7 looks like this:
#i updated root / UUID
title       Ubuntu 8.04.3 LTS, kernel 2.6.24.030320
root        (hd0,6)
kernel      /boot/vmlinuz-2.6.24.030320 root=UUID=551eca4c-0a08-4116-aaa7-16a8c3104932 ro quiet splash
initrd      /boot/initrd.img-2.6.24.030320
quiet

```

#drive layout:
```

sudo fdisk -l

#first ubuntu installation

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       19457    74364885    5  Erweiterte
/dev/sda5           10200       10260      489951   82  Linux Swap / Solaris
/dev/sda6           10261       18042    62508883+  83  Linux
/dev/sda7           18043       19391    10835811   83  Linux
/dev/sda8           19392       19457      530113+  82  Linux Swap / Solaris

#second one, residing on external usb drive

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1       30027   241191846   83  Linux
/dev/sdb2           30028       30401     3004155    5  Erweiterte
/dev/sdb5           30028       30401     3004123+  82  Linux Swap / Solaris

```


Would that work?

---

### Post by metalfan_ on 2009-09-08
It did work with some modifications:

/boot/grub/menu.lst needs to be updated on the target drive. UUID/root needs updating.

---


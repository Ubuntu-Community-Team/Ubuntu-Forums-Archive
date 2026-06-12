---
title: "problem with installing custom kernel in ubuntu 8.04"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by ssnkrn on 2009-02-02
My aim is to run Xen-supported linux kernel in the Ubuntu 8.04.  I downloaded the linux tree(with inbuilt Xen support) and tried installing it

This is what I did :

- copied config from /boot to linux source directory
- make oldconfig
- make
- make modules
- make modules_install
- make install

After this the vmlinuz image and the other files like System.map, config etc got copied to /boot.  The grub was not updated so i wrote my own entry there.
```
title           Ubuntu 8.04.2, kernel 2.6.18-8-xen-3.3
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.18.8 root=UUID=aab5a576-1b4f-49c6-b169-93da126e1774 ro quiet splash
initrd          /boot/initrd.img-2.6.18.8
quiet
```

When I reboot the system and select this kernel, it says "Error 13: Invalid or unsupported executable format" 

I read through a lot of answers in many forums for this problem but nothing helped...Any idea on the reason for this problem ?

I have NO OTHER operating Systems installed in the machine and I have two hard disks with ubuntu installed in one of them and the other holding a blank ext3 partition.

Thanks,
Sankar.

---

### Post by ssnkrn on 2009-02-03
I downloaded the source from [http://www.xen.org/download/](http://www.xen.org/download/)

---


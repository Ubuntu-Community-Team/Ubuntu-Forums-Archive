---
title: "[SOLVED] Grub Error 21 after external hardrive install"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by verbal.kint on 2008-12-23
I have 7.10 on my internal harddrive on a 14GB partition. I was installing 8.10 on a partition on my external hard drive but after the install i get an ERROR 21 at the grub boot loader when the external drive is NOT plugged in and an ERROR 17 when the external harddrive IS plugged in. I am talking to you from an 8.04 live cd because it will allow me use the wireless.

my grub.menu from my original 7.10 install is:
```
title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=499840b7-d5ea-4776-9542-8e45b7b569e8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

and the device.map for the same install is ```
(hd0)	/dev/sda
```

---

### Post by verbal.kint on 2008-12-23
solved my own problem, i reinstalled the grub loader using the instructions here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

the menu.lst looks pretty much the same though so i dont know what the problem was

---


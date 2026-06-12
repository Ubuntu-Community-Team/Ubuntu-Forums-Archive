---
title: "Failed to mount root device"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by arekku on 2009-11-08
For some reason kernel 2.6.32.14.27 will not mount the root device. 

The contens of my menu.lst file is
```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        1b5738b1-8683-4a71-93af-194e4946a04a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1b5738b1-8683-4a71-93af-194e4946a04a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        1b5738b1-8683-4a71-93af-194e4946a04a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1b5738b1-8683-4a71-93af-194e4946a04a ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        1b5738b1-8683-4a71-93af-194e4946a04a
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1b5738b1-8683-4a71-93af-194e4946a04a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        1b5738b1-8683-4a71-93af-194e4946a04a
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1b5738b1-8683-4a71-93af-194e4946a04a ro  single
initrd        /boot/initrd.img-2.6.28-16-generic
```

As seen above 28-16 (which works) uses the same boot parameters bar kernel file, making me suspect that something changed in the way partitions are designated, and fixing the grub parameters will make 31-14 boot.

---

### Post by arekku on 2009-11-09
I reckon credit is due to [this guy](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

By simply replacing the new initramfs with the old working file the OS now boots. I even got the sound back.

---


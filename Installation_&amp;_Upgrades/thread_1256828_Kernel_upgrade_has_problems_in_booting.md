---
title: "Kernel upgrade has problems in booting"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by hey_ram on 2009-09-03
Hello all,

I went through the master kernel thread and tried to compile and boot from the latest kernel. the amount of space on my system is very low, so low that i am unable to "make" the kernel after un-tarring it and still have some space left.

so i formatted an external hard drive partition to ext3 and loaded and compiled the kernel on that. to load the OS from that kernel, i edited /boot/grub/menu.lst. the particular entry about the latest kernel looks something like this:

```

#This is for the new kernel.
title      Ubuntu 8.04.1, kernel 2.6.30.5-generic
root       (hd0,5)
kernel     /boot/vimlinuz-2.6.30.5 root=/dev/sdb8
initrd     /initrd.img-2.6.30.5

```

when i reboot the system, i get the following error message:
Error 15: File not found

I know that the above lines in menu.lst, especially initrd is incorrect.

From the above lines of menu.lst:
1. root: this was root specified for all the other operating systems, so i think this must be where the other kernels get their files for loading the operating system.

2. kernel: the partition on the external hard drive where the kernel is loaded is /dev/sdb8 (i checked it using GParted).

3. initrd: since the kernel was compiled on the external hard drive, I do not know what the initrd for it would be, and if at all I have created an image for the kernel. 

Any help in solving this problem would be most welcome. i did check other forums on the internet and could not come across this particular instance of the problem.

thanks.

---

### Post by hey_ram on 2009-09-05
***bump****

---


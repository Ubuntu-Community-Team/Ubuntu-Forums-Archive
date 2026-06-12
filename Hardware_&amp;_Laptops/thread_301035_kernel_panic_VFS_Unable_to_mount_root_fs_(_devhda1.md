---
title: "kernel panic: VFS: Unable to mount root fs ( /dev/hda1 )"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by neocookie on 2006-11-16
Trying to install the k7 kernel, I get the following error: ```
VFS: Cannot open root device "hda1" or 03:01
Please append a correct "root=" boot option
Kernel panic: VFS: Unable to mount root fs on 03:01
```

Here's my menu.lst: ```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.4.27-2-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.4.27-2-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.4.27-2-k7
quiet
savedefault
boot

title		Ubuntu, kernel 2.4.27-2-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.4.27-2-k7 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.4.27-2-k7
boot

```

Can't see what the difference is compared to generic. Am I missing something?

---


---
title: "w2k not in menu"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by philetus on 2008-12-14
I have been trying for 3 days to dual boot w2k and Intrepid.
I have tried all the "sure fire" methods with no luck.
Would someone please help?

output of menu.lst
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5786917c-7292-4062-922b-605ca04b1c27
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5786917c-7292-4062-922b-605ca04b1c27 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		5786917c-7292-4062-922b-605ca04b1c27
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5786917c-7292-4062-922b-605ca04b1c27 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5786917c-7292-4062-922b-605ca04b1c27
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5786917c-7292-4062-922b-605ca04b1c27 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5786917c-7292-4062-922b-605ca04b1c27
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5786917c-7292-4062-922b-605ca04b1c27 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5786917c-7292-4062-922b-605ca04b1c27
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by philetus on 2008-12-15
Needless to say, I formatted and started over again.
I have a working dual boot setup now, thanks to me.

---


---
title: "Chainloading help"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Ouia on 2009-03-05
Hi there,

Recently I put UbuntuStudio on my computer, after I already had Ubuntu 8.04 installed.
I used separate partitions for this.

Now, I got the advice to use a chainloader for kernel updates (I'm guessing because Ubuntustudio does not let me use wireless), but I'm not very well known with GRUB.
(So far, I managed to get the computer to boot the first install(8.04) first, by changing /media/disk/boot/grub/menu.lst)

From what I did read about chainloading, there must be something changed with in the same file, so here is what it looks like.

Thanks.


```

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=7fbbcbb3-d0ae-46ae-9312-13ecdd1667b0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=7fbbcbb3-d0ae-46ae-9312-13ecdd1667b0 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f1287190-73b6-418f-afd1-65655a07119f ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		64studio, kernel memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by Ouia on 2009-03-06
Anybody?

---


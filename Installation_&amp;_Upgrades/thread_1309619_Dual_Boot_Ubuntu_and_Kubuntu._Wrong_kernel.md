---
title: "Dual Boot: Ubuntu and Kubuntu. Wrong kernel?"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by AlanInVancouverBC on 2009-11-01
With respect to kernels, I  don't understand why when I updated (vs clean install) to 9.10, the grub still shows 9.04 kernels. Yet I'm booting to 9.10!
So???
Here are my kernels. The first are the Kubuntu kernels, followed by the Ubuntu kernels. Note that the Ubuntu show 9.04, but both OSs are 9.10. My computer boots to Kubuntu, regrettably, so I edit in Kubuntu, using Kate, to edit Menu.lst.
And as this thread indicates, it is with Ubuntu that I can't get sound.

## ## End Default Options ##

title Ubuntu 9.10, kernel 2.6.31-14-generic
uuid 8b80c990-2229-481f-a2a3-408ab5e608e6
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=8b80c990-2229-481f-a2a3-408ab5e608e6 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
quiet

title Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid 8b80c990-2229-481f-a2a3-408ab5e608e6
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=8b80c990-2229-481f-a2a3-408ab5e608e6 ro single
initrd /boot/initrd.img-2.6.31-14-generic

title Ubuntu 9.10, kernel 2.6.28-11-generic
uuid 8b80c990-2229-481f-a2a3-408ab5e608e6
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=8b80c990-2229-481f-a2a3-408ab5e608e6 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid 8b80c990-2229-481f-a2a3-408ab5e608e6
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=8b80c990-2229-481f-a2a3-408ab5e608e6 ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.10, memtest86+
uuid 8b80c990-2229-481f-a2a3-408ab5e608e6
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro quiet splash vga=792
initrd /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro single
initrd /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro quiet splash vga=792
initrd /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro single
initrd /boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro quiet splash vga=792
initrd /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro single
initrd /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 9.04, memtest86+ (on /dev/sda1)
root (hd0,0)
kernel /boot/memtest86+.bin
savedefault
boot

---

### Post by AlanInVancouverBC on 2009-11-11
I just fixed it by installing (vs upgrading) Ubuntu 9.10 over Kubuntu. Now I have a warped Ubuntu 9.10 on one HD and a good Ubuntu 9.10 on the other HD--booting to the good 9.10.

---


---
title: "New Kernels freezing Ubuntu when getting to login screen"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by Omeil on 2009-04-03
Hi all, I have been trying to figure out what is wrong with this issue but to no luck, I reinstalled Ubuntu and ran the updates again and I'm back to where I started all new kernels don't work, only the -7 version of the kernel works with comes packed with the Ubuntu installation. When I try to run any of the new kernels I either get the black screen or a distorted screen. As seen in the attachment.

Grub:

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		62f1cab9-3198-4211-8cf2-fc55c38049e8
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=62f1cab9-3198-4211-8cf2-fc55c38049e8 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		62f1cab9-3198-4211-8cf2-fc55c38049e8
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=62f1cab9-3198-4211-8cf2-fc55c38049e8 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		62f1cab9-3198-4211-8cf2-fc55c38049e8
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=62f1cab9-3198-4211-8cf2-fc55c38049e8 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		62f1cab9-3198-4211-8cf2-fc55c38049e8
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=62f1cab9-3198-4211-8cf2-fc55c38049e8 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		62f1cab9-3198-4211-8cf2-fc55c38049e8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=62f1cab9-3198-4211-8cf2-fc55c38049e8 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		62f1cab9-3198-4211-8cf2-fc55c38049e8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=62f1cab9-3198-4211-8cf2-fc55c38049e8 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		62f1cab9-3198-4211-8cf2-fc55c38049e8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Gentoo Base System release 1.12.11.1 (on /dev/sda3)
root		(hd0,2)
kernel		/boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda3 
initrd		/boot/initramfs-genkernel-x86-2.6.24-gentoo-r5
savedefault
boot

```

As with Xorg.conf I tried reverting back to the original (vesa) but the same issue happens. Could it be that my Ubuntu source has corrupt updates?

Kind Regards,

Omeil

---


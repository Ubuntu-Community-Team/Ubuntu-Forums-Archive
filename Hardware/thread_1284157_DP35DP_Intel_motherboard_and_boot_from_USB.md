---
title: "DP35DP Intel motherboard and boot from USB"
date: 2009-10-06
forum: Hardware
---

### Post by Joe_Bishop on 2009-10-06
Did anyone manage to boot from USB device natively? I tried to boot with my USB stick, but always get "Boot error" followed by standard boot sequence. The only way to boot with USB device is to use GRUB and enter something like
```
> root (fd0)
> kernel /casper/vmlinuz file=preseed/ubuntu.seed boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash
> initrd /casper/initrd.gz
> boot
```
in a GRUB console. I have now grub live cd for these, but it would be nice to find out how to boot natively if it's possible.

---

### Post by gewalker on 2011-10-21
I am having the same issue and I think this bug is relevant (and contains a possible fix although I haven't had a chance to test it yet):

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458482](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458482)

---


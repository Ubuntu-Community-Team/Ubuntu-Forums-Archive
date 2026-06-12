---
title: "[wip] Community guide to Ubuntu 16.10 on Linx 1010B (help needed)"
date: 2016-10-10
forum: Hardware
---

### Post by jordan-j on 2016-10-10
[CENTER]The community guide to Ubuntu 16.10 on [Linx 1010B]("https://www.amazon.co.uk/gp/product/B014D847FS?ie=UTF8&camp=1634&creativeASIN=B014D847FS&linkCode=xm2&tag=quantumhostin-21")

[/CENTER]
Sections:



[LIST]
[*]1. Downloading the latest pre-built image for USB (under development)
[*]2. The installation proceedure
[*]3. Installing drivers and required software packages
[/LIST]


1. Downloading the latest pre-built image for USB (under development)

This is currently under development and can boot from usb, install onto eMMC and support wired keyboard.

Before the image can be deemed ready for upload, an issue stands in the way; we need to boot the image to install extra packages for grub to work in a 32-bit EFI on a 64-bit OS.

Solution: add the following into the /boot/grub.cfg (apart from it does not boot, drive is found, but kernel is not.)

```
menuentry "Run from internal disk" {    
    linux    (hd1,gpt1)/boot/vmlinuz-4.8.0-14-generic.efi.signed root=/dev/mmcblk1p1 intel_idle.max_cstate=0 quiet splash $vt_handoff
    initrd    (hd1,gpt1)/boot/initrd.img-4.8.0-14-generic
   }

```

So before adding the next part to this guide / uploading the USB image, ways to determine the correct boot information is needed. Please comment suggestions below.

---


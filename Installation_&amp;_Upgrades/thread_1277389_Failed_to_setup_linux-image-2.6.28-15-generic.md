---
title: "Failed to setup linux-image-2.6.28-15-generic?"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2009-09-28
I am running mythbuntu 9.04 and everytime I do sudo apt-get update and sudo apt-get upgrade I get these messages.

Setting up linux-image-2.6.28-15-generic (2.6.28-15.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
cpio: ./etc/modprobe.d/oss-compat.conf: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-15-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone explain why it appears to not be working? WHen I do uname -r, it does list this:
2.6.28-15-generic

Very strange. Any help would be appreciated.

---

### Post by Soul-Sing on 2009-09-28
Did you made a [COLOR="Magenta"]manually[/COLOR] video driver update?

---


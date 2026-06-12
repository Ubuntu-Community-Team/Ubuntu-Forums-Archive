---
title: "initramfs script"
date: 2006-01-22
forum: Installation &amp; Upgrades
---

### Post by scotty boy on 2006-01-22
Hey,

im currently trying to install ubuntu to an external hard drive enclosure and have made a initramfs image to boot it. Unfortunately although the usb support for the drive loads, the image tries to boot the drive too early - before the drive is recognised.  It then crashes to a shell and only a few seconds later it is recognised.

I am convinced this is just a timing problem and was wondering where I could insert a sleep command in the boot script(and where it is), between when the usb support is loaded and booting?

Thanks

--- Marty

---


---
title: "If you are having trouble compiling modules..."
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by ceekay on 2005-01-24
I was having trouble compiling modules, like lirc-modules-source and the newest orinoco drivers. I had the kernel source, the /usr/src/linux symlink, and the .config file from /boot/config-<version> but it had some crazy errors whenever I tried to compile. I couldn't figure out what was wrong! For some reason, the only thing that fixed it was doing a cd /usr/src/linux and running make. You don't have to copy the new kernel or install or anything, just running make seems to something that makes other compiles work. Hopefully I can save someone else some time!

---

### Post by az on 2005-01-24
A pristine kernel source is not what you need to compile modules.  You need a matching kernel source, and that means that the .config is exactly the same as the one you are running.

You need to unpack your kernel tree and copy the config file of your running kernel from /boot.  You then need to compile at least the kernel headers so that the new module's source you want to use will have something to work with.

To build just the kernel headers is a pain in the ass.  Just install the headers, as they are already prepackaged.  If you mae your own kernel with kernel-package, you can make yourself the headers with the kernel_headers option as well as the kernel_image.

The Ubuntu packages for the kernel headers are called linux-headers.

---


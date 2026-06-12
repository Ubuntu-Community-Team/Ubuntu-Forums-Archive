---
title: "custom build kernel"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by wrexy on 2005-12-26
I am not sure how to go about adding modules to stock 2.6.12-10-686 kernel.

I apt-get install linux-source-2.6.12 and linux-patches-2.6.12-10.25

Does linux-source-2.6.12 only contain unbuntu kernel source 2.6.12? In order to get to kernel 2.6.12-10 or above, I have to patch linux-patch-2.6.12-10.25 to the linux-source-2.6.12 directory? Can someone show how this is done?

I follow wiki page by doing

bunzip2 linux-patches/i386/2.6.12/debian/patches-2.6.12-10.25.bz2

and then

cd /usr/src/linux
patch -p1 < /usr/src/linux-patches/i386/2.6.12/debian/patches-2.6.12-10.25

Howhowever, there was a lot messages, saying whether that was a reverse patch or file is already there.

Some kernel how-to recommend to compile into necessary driver in order to do without initrd image. What is the proper way to achieve this?

Should we use fakeroot make-kpkg to compile the kernel into deb package or just do make && make modules_install install?

Wrex

---


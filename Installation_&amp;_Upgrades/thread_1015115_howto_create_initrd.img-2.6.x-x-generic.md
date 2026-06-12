---
title: "howto create initrd.img-2.6.x-x-generic ?"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by seeking_that on 2008-12-18
Hi,

I built a kernel image using make-kpkg as follows 

a) downloaded the latest stable ubuntu kernel source (hardy)
b) ran the following command
make-kpkg --initrd --mkimage initrdimage --rootcmd fakeroot --append-to-version=-generic --bzimage

but it did not build the initrdimage 

How can I build the initrd image ?

The kernel that I built doesn't boot with the current version of initrd.img-2.6.24.22-generic for which the kernel was built.

I see that the system hangs while mounting the disks.

Could anybody give me an insight as to why it is happening and how do I make the kernel that I built boot ?

Thanks,
seeking that

---


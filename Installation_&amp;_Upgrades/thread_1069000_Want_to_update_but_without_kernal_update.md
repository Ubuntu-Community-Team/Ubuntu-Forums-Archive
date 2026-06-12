---
title: "Want to update but without kernal update"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by delboy1 on 2009-02-13
I am still persevering with Ubuntu on my Dell Mini and am re-installing (lost count of how many times now :P) 8.10.

When I install it I get notification of some 250 odd files to be updated, part of which is the new kernel 2.6.27-11. However, that causes network problems so I do not want to update it. How do I stop the updater installing it - what files do I untick.

Thanks

---

### Post by lemming465 on 2009-02-14
I think you have two good options here.  The first is to just have multiple kernels installed, and boot the one that works.  That may be easier if /boot/grub/menu.lst specifies *default saved*.

The other is to go into synaptic, find the linux-image file corresponding to the kernel you like, select it, and pick Packages -> Lock Version.

---


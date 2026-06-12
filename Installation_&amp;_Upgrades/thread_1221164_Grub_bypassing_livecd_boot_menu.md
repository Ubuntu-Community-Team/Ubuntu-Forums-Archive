---
title: "Grub bypassing livecd boot menu"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by Malefic on 2009-07-23
I have an external hardrive which I have installed grub onto. Now I'm copying various livecd's onto the disk so I can do all my installations from one external harddrive.

My problem is that I don't get the livecd boot menus when they are started using grub. The livecd will just boot straight into the live desktop.

This is how my current grub is addressing the livecd partition:

```

title		Ubuntu 9.04 Desktop LiveCD (x86)
kernel		(hd0,4)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
initrd		(hd0,4)/casper/initrd.gz 

```

Does anyone know what I have to change to get the livecd menu to display?

---

### Post by Malefic on 2009-07-23
bump

---


---
title: "software update but menu.lst not updated"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by BattlePanic on 2009-07-06
I am running Intrepid 8.10 and just recently performed a software update.  Among the updates were updated kernel headers.  Usually this update also modifies the file /boot/grub/menu.lst.  During the update I was asked whether I wanted to keep the old version of menu.lst or replace it or open a shell.  I chose to open the shell and then copied my current menu.lst to make a backup.  I then exited the shell and the update completed.

Now it looks like the menu.lst was not updated.  It is still the same as my backup.  I'm assuming that I need an updated menu.lst if I'm going to be booting the new kernel version that was included in the update.  Is there some place I can find a copy of this updated menu.lst file?

---

### Post by wojox on 2009-07-06
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		3b5556e5-b036-4c28-8779-34028bb4abc8
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3b5556e5-b036-4c28-8779-34028bb4abc8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		3b5556e5-b036-4c28-8779-34028bb4abc8
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3b5556e5-b036-4c28-8779-34028bb4abc8 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3b5556e5-b036-4c28-8779-34028bb4abc8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3b5556e5-b036-4c28-8779-34028bb4abc8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3b5556e5-b036-4c28-8779-34028bb4abc8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3b5556e5-b036-4c28-8779-34028bb4abc8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3b5556e5-b036-4c28-8779-34028bb4abc8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by drs305 on 2009-07-06
This command should add the new kernels to your menu.lst:
```

sudo update-grub
```

Assuming you meant Intrepid 8.10.

---

### Post by BattlePanic on 2009-07-10
I never knew about the update-grub utility.  Thanks for the tip.

---


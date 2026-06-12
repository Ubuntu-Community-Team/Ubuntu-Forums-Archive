---
title: "Problems updating a kernel"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by bgbnbigben on 2009-07-20
Hey all,

So i've recently decided to configure my own kernel, but have been doing little more than giving myself numerous headaches and making me wonder why i ever bothered.
However, having nothing better to do with my time leads me to keep trying :-P

After having no luck with building 2.6.30.1 (i copied my /boot/config-2.6.28-13-generic over to /usr/src/linux-2.6.30.1/.config and tried ```
 sudo make all && sudo make modules_install && sudo make install; cd /boot/; sudo mkinitramfs -o initrd.img-2.6.30.2-1337homebrew 2.6.30.2; sudo update-grub; 
```, but that still didnt work), i tried much of the same thing with 2.6.30.2, and have gotten the same error at bootup:
```
 Kernel Panic - Not Syncing: VFS: unable to mount root fs on unknown-block(0,0)
```

I trawled through /boot/grub/menu.lst just to make sure it was mounting the correct filesystem, etc. etc. and by the looks of things it was all good - which really only leaves the possible explanation of removing my hard-drive drivers from the kernel, but i just straight copy-pasted an existing config file, so that should be no issue.
I dont believe it's anything to do with hardware; im able to boot into 2.6.28-13-generic with no problems (and i havent bothered booting into *-11-generic, but ill also assume that that works).

Does anyone have any ideas on what's going wrong?
cheers

---

### Post by bgbnbigben on 2009-07-21
bump

---

### Post by bgbnbigben on 2009-07-22
gah, cant someone help?! i hate bumping my own threads!

---


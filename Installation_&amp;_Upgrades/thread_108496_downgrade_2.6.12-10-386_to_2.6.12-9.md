---
title: "downgrade 2.6.12-10-386 to 2.6.12-9"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by meckatzermichel on 2005-12-26
i automatically upgraded my kernel, as ubuntu requested.
but now i need the old kernel, because truecrypt won't install.
how can i downgrade easily to the old kernel ?

thanks in advance
meckatzermichel

---

### Post by Sutekh on 2005-12-26
When you updated your kernel to the -10-386, it should have left the old kernel there, unless you removed it yourself.  The option to boot the -9-386 kernel would still be in the GRUB menu.  

When GRUB appears at boot up choose to boot Ubuntu with the 9-386 kernel *not* the -10-386 kernel (which will be the default).  Leave both there and get the best of both worlds.  

If you did remove the old kernel then you can still get it through apt get
```
sudo apt-get install linux-image-2.6.12-9-386
```
Or look it up in Synaptic.

It's perfectly possible to have as many kernels as you can fit on your hard drive all installed, and you just choose the one you wish to use at each boot up.

---

### Post by meckatzermichel on 2005-12-26
thanks. that's great. i don't know why i haven't recognized it at reboot.....
perhaps i should wear my glasses. ;-)

meckatzermichel

---


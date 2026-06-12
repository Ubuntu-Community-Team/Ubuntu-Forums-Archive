---
title: "Too many kernels to boot at startup"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by babujbf on 2008-12-16
I have a dual boot computer Ubuntu Hardy/Windows Xp and for some reasen I know have like 4 options to pick to boot for ubuntu, different versions of kernels each with its own recovery option. And I originally had Ubuntu, Recover and Windows.

How can I just choose the lastest kernel and delete the rest?

---

### Post by taurus on 2008-12-16
When you update a kernel, you will get two entries in /boot/grub/menu.list (one for normal boot and one for recovery mode).  So if you have two kernels, you would have four entries.  It's a good idea to leave the previous working kernel on your machine when you upgrade to a newer kernel in case the newer one goes belly up.  But if you want to remove it, then you can do so from synaptic and then edit /boot/grub/menu.lst and remove those entries for the older kernel.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by babujbf on 2008-12-16
thanks, yeah but I had six and I dont know how so I just deleted the middle one

---

### Post by taurus on 2008-12-16
If you just delete some entries in /boot/grub/menu.lst, those older kernels are still resided on your machine.  You have to use synaptic to remove them if you want to free up the space in /boot.

```
uname -a
ls -la /boot
```

---


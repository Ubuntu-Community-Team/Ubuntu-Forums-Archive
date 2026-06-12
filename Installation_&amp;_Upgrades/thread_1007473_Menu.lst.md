---
title: "Menu.lst"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by Alan F on 2008-12-10
I have just upgraded, online, from 8.04 to 8.10, apparently without problems.

However during the installation I was given the option to retain the existing modified /boot/grub/menu.lst. This, unfortunately (stupidly), I did.

Thus the current installed menu.lst refers to old 8.04 files.

How can I obtain a copy of the correct, standard, 8.10 menu.lst? Or at least the correct text?

---

### Post by Kevbert on 2008-12-10
You want the kernel version:
```
title		[COLOR="Red"]Ubuntu 8.10, kernel 2.6.27-9-generic[/COLOR]
uuid		bbf94cbb-78b2-4015-8e32-47b84daada2d
kernel		/boot/vmlinuz-[COLOR="Red"]2.6.27-9[/COLOR]-generic root=UUID=bbf94cbb-78b2-4015-8e32-47b84daada2d ro quiet splash 
initrd		/boot/initrd.img-[COLOR="Red"]2.6.27-9[/COLOR]-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		bbf94cbb-78b2-4015-8e32-47b84daada2d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=bbf94cbb-78b2-4015-8e32-47b84daada2d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic
```
You just need to change anything shown in red. Your UUID will stay the same as in 8.04.

---

### Post by Alan F on 2008-12-10
Thank you.):P

---


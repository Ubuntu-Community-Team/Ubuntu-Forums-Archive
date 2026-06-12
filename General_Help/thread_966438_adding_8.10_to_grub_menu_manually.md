---
title: "adding 8.10 to grub menu manually"
date: 2008-11-01
forum: General Help
---

### Post by jdrodrig on 2008-11-01
I just finished upgrading from 8.04 to 8.10 but I am afraid I might have click OK to keep my grub menu as it is, during the installation. Now 8.04 is still the only option I see in the grub boot menu, how can I manually add the 8.10 to that list?

could you kindly copy-paste your menu.lst? I mean, the part that mentions 8.10....

---

### Post by Sealbhach on 2008-11-01
Here is mine:

```
title		Ubuntu 8.10 Intrepid Ibex
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=32ffc4e1-1f89-4feb-a63a-80f5fb322dc9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=32ffc4e1-1f89-4feb-a63a-80f5fb322dc9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

```

Your UUIDs may be different, I don't know the command to find them but I'm sure it's easy.

EDIT:
Here is the command:

```
 blkid

```

.


.

---

### Post by jdrodrig on 2008-11-01
noob question, can I just copy paste the UUID from my other Ubuntu kernels in my current menu.lst?

---

### Post by Kevbert on 2008-11-01
Basically you need to change or copy the new kernel information. Old information:
```
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ac4f091c-d379-475c-8f76-b6e9ca0b5865 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
```
will now become
```
title		[COLOR="Red"]Ubuntu 8.10, kernel 2.6.27-7-generic[/COLOR]
root		(hd1,6)
kernel		/boot/vmlinuz-[COLOR="Red"]2.6.27-7[/COLOR]-generic root=UUID=ac4f091c-d379-475c-8f76-b6e9ca0b5865 ro quiet splash
initrd		/boot/initrd.img-[COLOR="Red"]2.6.27-7[/COLOR]-generic
quiet
```
Changes are shown in red. The 'title' information is what you see on the screen when you boot up.

---


---
title: "to many boot options"
date: 2008-10-22
forum: General Help
---

### Post by rasmus91 on 2008-10-22
Hi

I use Intrepid beta, and i have a little problem which have also occurred to me before, each time the kernel updates, it'll add something like 2 more boot options, i think you can guess that this makes a lot of possibilities over time.

so what i wanna know is, how do i remove some of these many boot options?

---

### Post by northern lights on 2008-10-22
The GRUB boot menu resides in /boot/grub/menu.lst

To manually edit this file, make a backup```
cp /boot/grub/menu.lst /boot/grub/menu.lst_bkup
```and edit with```
gksu gedit /boot/grub/menu.lst
```Uncommenting (removing the hash/#) the following```
# howmany=all
```and changing all to the number of kernels you want to keep does the trick. You can of course just manually delete redundant kernels after every upgrade.

The GUI way is through "System > Administration > StartUp-Manager".

---

### Post by hyper_ch on 2008-10-22
actually better way is to remove the old kernels... I'd always keep at least the second latest and latest one... second latest so you can fallback in case you discover a problem with the latest one.

Open synaptic, seach there for "2.6.27" --> remove & purge the older ones that you don't need anymore.

---


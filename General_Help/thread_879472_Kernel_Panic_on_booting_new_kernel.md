---
title: "Kernel Panic on booting new kernel"
date: 2008-08-04
forum: General Help
---

### Post by karthikb23 on 2008-08-04
Hi,
I compiled a kernel (2.6.11-1). Thereafter, i performed 'make modules' and 'make modules_install'.
Everything worked fine, and unlike other instructions (using make_kpkg), i copied the file 'bzImage' from arch/i386/boot, and placed it in '/boot/mykernel'.

I then updated GRUB's menu, and added an entry exactly like my old kernel, except chainging my kernel name to 'mykernel'.

On the first boot, i got a kernel panic, as it was unable to locate any modules.
I came across a suggestion to disable 'initrd', and deleted the initrd line from GRUB's menu.

Now on a boot, i get a kernel panic stating 'Wrong Device'.

Any suggestions please?

Thanks in advance!!

---


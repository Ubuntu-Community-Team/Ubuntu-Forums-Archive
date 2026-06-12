---
title: "Generic Kernel or x86, which is better ?"
date: 2008-07-25
forum: Hardware
---

### Post by Julian David Pitt on 2008-07-25
I am using the 2.6.24.19 generic kernel in my IBM T23 laptop and I would like to know should I install the x86 version as that would seem to be the correct kernel for my hardware? I would also like to know how to remove the old kernel versions from the laptop as I have versions 2.6.22.16, 17 and 18 still showing in grub when the laptop starts up. Thanks in advance people.

---

### Post by ilrudie on 2008-07-25
> **Julian David Pitt said:**
> I am using the 2.6.24.19 generic kernel in my IBM T23 laptop and I would like to know should I install the x86 version as that would seem to be the correct kernel for my hardware? I would also like to know how to remove the old kernel versions from the laptop as I have versions 2.6.22.16, 17 and 18 still showing in grub when the laptop starts up. Thanks in advance people.

The generic kernel is compiled for x86 (or x86_64/AMD64 depending on 32 vs 64-bit hardware).  There isn't a special kernel you need.  If you kernel was compiled for a different architecture it wouldn't run.

Old kernel versions can be uninstalled using synaptic and they can be removed from grub (if the uninstall doesn't do it or for some reason you don't want to uninstall them) by editing (as root) the /boot/grub/menu.lst file.  _**Always make a backup before editing important system configureation files.**_  Lines beginning with # are comments like normal.  **Make sure to remove whole stanzas** or it may mess up your boot process requiring you to boot from cd and fix the file before grub will work properly again.

---


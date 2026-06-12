---
title: "[SOLVED] Clean-up kernel versions after updates"
date: 2008-12-01
forum: General Help
---

### Post by Cariboo1938 on 2008-12-01
My Installation is:
Ubuntu 8.04.1 Codename: hardy

After the last update the system runs under:
Linux kernel 2.6.24-**[COLOR="Magenta"]22[/COLOR]**-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux

Synaptic Package Manager shows that a few "linux 2.6.24-***[COLOR="Magenta"]21[/COLOR]*** - packages" (linux-headers, linux-image, linux-restricted-modules)
are still installed and I wonder what they are needed for and if I could un-install them to save space
on the 4 GB partition I have left for the Ubuntu OS. :confused:

---

### Post by cpetercarter on 2008-12-01
Yes, you can remove them. However, I always prefer to keep one earlier kernel on my computer, so that I can boot using it if the new kernel proves troublesome.

---

### Post by binbash on 2008-12-01
Yes you can remove previous kernels safely but i suggest keeping at least 2 kernels.

---


---
title: "Modules not compiled for the running kernel"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by leezer3 on 2005-07-12
Hi guys,
For some reason that I cannot fathom, my kernel source is set up correctly, but modules will *still* not compile :(
This means that I have done some poking on Google to find precompiled modules, for the two drivers that I'm missing- IPW2100 & SLMDM. I've found .deb files for both of these, and retrieved the necessary .ko files. My problem comes when I try to load them with modprobe etc, as Ubuntu tells me that they are an **Invalid Module Format**. 
Again with some searching etc, I find that this is because these have not been compiled for the running kernel version. Any way I can hack this please? (Kver: 2.6.10-686)

Thanks

-Leezer-

---

### Post by jaranguren on 2005-07-12
There is an option when you compile your kernel to enable support for modules compiled from a different kernel version.  But this means you'd have to recompile your kernel and enable "Module Versioning Support" under "Loadable module support".

Here's some more info:

  &#9474; Usually, you have to use modules compiled with your kernel.             &#9474;
  &#9474; Saying Y here makes it sometimes possible to use modules                &#9474;
  &#9474; compiled for different kernels, by adding enough information            &#9474;
  &#9474; to the modules to (hopefully) spot any changes which would              &#9474;
  &#9474; make them incompatible with the kernel you are running.  If             &#9474;
  &#9474; unsure, say N.

---


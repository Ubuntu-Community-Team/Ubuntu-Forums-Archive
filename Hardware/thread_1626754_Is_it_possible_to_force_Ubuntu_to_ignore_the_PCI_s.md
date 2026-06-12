---
title: "Is it possible to force Ubuntu to ignore the PCI slots?"
date: 2010-11-20
forum: Hardware
---

### Post by ahorriblemess on 2010-11-20
Is it possible to force Ubuntu to ignore the PCI x16 slot so I can continue to use the on-board graphics even if a GPU is installed to my computer's motherboard?

I'll spare the reason why I want to do this, I just want to know if it's possible and if so, how to do it. I don't want this thread to veer off topic either.

---

### Post by nerdy_kid on 2010-11-20
I don't think so (unless you want to manually write a patch for the kernel...)

---

### Post by wakko_kid on 2010-11-20
The way could be to find out if the part of the kernel in charge of PCIex communication is compiled as a kernel module.

-If is compiled as a module, you should find out which module is and add it to the module blacklist.

-If it is not compiled as a module, you should get a kernel source, configure it, recompile it leaving out that part of kernel.

Hoping that this is feasible :p

By the way: doing this you will disable ALL PCIex slots! Have you other PCI devices?

Bye.


P.S.:
Are you sure that in your bios there is not the option to force the use of integrated graphics?
I have seen this option in many PCs.

---

### Post by cascade9 on 2010-11-20
> **wakko_kid said:**
> By the way: doing this you will disable ALL PCIex slots! Have you other PCI devices?

Which means that it would also disable most SATA controllers.

---


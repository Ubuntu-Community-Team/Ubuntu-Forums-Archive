---
title: "amd ati r7 260x driver not supported"
date: 2014-02-25
forum: Hardware
---

### Post by chad5 on 2014-02-25
Hi there, i have 2x r7 260x graphics card.
I tried to install ati catalyst from there website, there latest version. But when i `sh` the catalyst loads up then i click on install.
It then says your graphics card is not supported with this driver. Even though it states that it does support it. I have also tried the beta version as well. But same problem.
Anyone installed this graphics card before? Or anyone know why it would do this?

Ubuntu 13.10
Linux headers 13.12
xorg 6.9

Thanks
Chad

---

### Post by Yellow Pasque on 2014-02-25
I'm curious as to the PCI ID of the cards:
```
lspci -v
```

---


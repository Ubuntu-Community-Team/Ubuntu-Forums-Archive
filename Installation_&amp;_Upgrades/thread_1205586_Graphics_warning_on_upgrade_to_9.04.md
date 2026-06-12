---
title: "Graphics warning on upgrade to 9.04?"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by JimBuntu on 2009-07-06
Why is it that I get this warning talking about my graphics driver for the ATI graphics card in my laptop when trying to upgrade Ubuntu? The driver is "ATI/AMD Proprietary FGLRX graphics driver". The warning says there is no version of this driver available for my hardware in Ubu 9.04 and that my screen resolution will be decreased. I'm running 8.10 and don't want to be stuck here... any suggestions?

---

### Post by gradinaruvasile on 2009-07-06
First of all what vid card model do u have?
type in a terminal:

```
lspci | grep VGA
```

and post the output of it.

---

### Post by JimBuntu on 2009-07-06
```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
```

---

### Post by Mark Phelps on 2009-07-07
> **JimBuntu said:**
> Why is it that I get this warning talking about my graphics driver for the ATI graphics card in my laptop when trying to upgrade Ubuntu?

It's telling you that to prevent you from forcing the installation of a restricted driver that will then render your video useless.

AMD/ATI dropped support for the older chipsets in their new drivers, including your chipset.  Thus, there really are NO restricted drivers available for your chipset that will run under 9.04.

---

### Post by JimBuntu on 2009-07-09
So, is that it? No more upgrading Ubuntu? Why can't I just use the same driver with 9.04 and beyond?

---

### Post by Mark Phelps on 2009-07-10
> **JimBuntu said:**
> So, is that it? No more upgrading Ubuntu? Why can't I just use the same driver with 9.04 and beyond?

Because the old drivers (the ones that work with the unsupported cards) are incompatible with the newer version of the XWindows server contained in Ubuntu 9.04.

This basically means that if you want hardware accelerated drivers, you have to stay with 8.10 -- where the old drivers and Xorg version are compatible.

---


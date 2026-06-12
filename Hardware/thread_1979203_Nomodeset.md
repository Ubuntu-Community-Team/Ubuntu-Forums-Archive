---
title: "Nomodeset"
date: 2012-05-12
forum: Hardware
---

### Post by awannabeee on 2012-05-12
nomodeset at boot is ok. after video driver is installed nomodeset left in grub list can cause problems.

i only have to use nomodeset on machines with embedded graphics that i have a card installed in. 

has anyone figured out how to point the kernel to the card, pci or pcie or agp or whatever the bus without having to use nomodeset?

                                      george ;}

---

### Post by wilee-nilee on 2012-05-13
If you actually put nomodeset in the kernel using-

```
 [FONT=Verdana, sans-serif][SIZE=1]gksudo gedit  /etc/default/grub[/SIZE][/FONT]
```It is removed the same way.

As far as pointing not sure really.

Using nomodeset is best done on in per-session basis with a edit at the grub menu.

---


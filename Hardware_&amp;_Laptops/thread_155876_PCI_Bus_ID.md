---
title: "PCI Bus ID"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by slipk487 on 2006-04-05
how do i find the pci bus id because i need to set up my ati graphics card and i dont know the bus id for were the graphics card is pluged in

---

### Post by henriquemaia on 2006-04-06
[QUOTE=slipk487]how do i find the pci bus id because i need to set up my ati graphics card and i dont know the bus id for were the graphics card is pluged in[/QUOTE]

From a terminal, run:

```
sudo X :1 -scanpci
```

Search on the list displayed your graphic card. You'll have the BusID Xorg style.

Hope this helps you.

---

### Post by slipk487 on 2006-04-06
i already figured it out

---


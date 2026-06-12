---
title: "PCI card"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by t-bag on 2007-06-06
I bought a usb/IEEE 1394a combo PCI card (radio shack brand) because my sony cam uses firewire to transfer video. 

Im on 6.06 and cant get it to work. Is it hopeless?

---

### Post by madmetal on 2007-06-07
> **t-bag said:**
> I bought a usb/IEEE 1394a combo PCI card (radio shack brand) because my sony cam uses firewire to transfer video. 

Im on 6.06 and cant get it to work. Is it hopeless?

open terminal and give 
lspci 
and see if you can find the card..
mine result is
```

02:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

```

and works perfect since 5.10 till gutsy testing..

UAResolved.

---


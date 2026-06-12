---
title: "HP USB 3.0 PCIex1 card question"
date: 2023-10-23
forum: Hardware
---

### Post by drichardson2 on 2023-10-23
Ubuntu 22.x lts user here

There is an HP kit to make certain HP desktops have USB 3.0 (that only have 2.0).  The kit comes with the hardware, obviously, and software driver installer(s) on cd/disk.  I'm sure the software installer isn't for Ubuntu/Linux.   Will Ubuntu recognize the hardware as USB or should I avoid this route

USB 3.0 as PCIex1 card that can be added is here:

[http://h10032.www1.hp.com/ctg/Manual/c02534104.pdf](http://h10032.www1.hp.com/ctg/Manual/c02534104.pdf)

---

### Post by jimmyrus on 2023-10-23
> **drichardson2 said:**
> Ubuntu 22.x lts user here

There is an HP kit to make certain HP desktops have USB 3.0 (that only have 2.0).  The kit comes with the hardware, obviously, and software driver installer(s) on cd/disk.  I'm sure the software installer isn't for Ubuntu/Linux.   Will Ubuntu recognize the hardware as USB or should I avoid this route

USB 3.0 as PCIex1 card that can be added is here:

[http://h10032.www1.hp.com/ctg/Manual/c02534104.pdf](http://h10032.www1.hp.com/ctg/Manual/c02534104.pdf)
Why don't you try it and find out? You're asking us about hardware that's fairly specialized, for only some models of HP, and all we know is that its for certain ones. Which ones you don't say. Installing it and finding out what happens would be quicker. If you have an actual problem with it, that's the time to post.

---

### Post by Yellow Pasque on 2023-10-23
It seems like you're referring to HP 608151-001: [https://www.amazon.com/HP-608151-001-SuperSpeed-PCIe-interface/dp/B008MO515U](https://www.amazon.com/HP-608151-001-SuperSpeed-PCIe-interface/dp/B008MO515U)
That card uses an NEC/Renesas D720200f chipset, which is fairly common and is used in all kinds of cards and laptops from different vendors.
It looks promising that this chipset has been supported in Linux for a long time: [https://linux-hardware.org/?id=pci:1033-0194-1033-0194](https://linux-hardware.org/?id=pci:1033-0194-1033-0194)

> **jimmyrus said:**
> You're asking us about hardware that's fairly specialized, for only some models of HP, and all we know is that its for certain ones.

I don't see anything special/custom with the card. It looks like an ordinary low-profile PCI-e x1 card with a SATA power connector, and should work in non-HP systems.

---

### Post by jimmyrus on 2023-10-24
> **Yellow Pasque said:**
> It seems like you're referring to HP 608151-001: [https://www.amazon.com/HP-608151-001-SuperSpeed-PCIe-interface/dp/B008MO515U](https://www.amazon.com/HP-608151-001-SuperSpeed-PCIe-interface/dp/B008MO515U)
That card uses an NEC/Renesas D720200f chipset, which is fairly common and is used in all kinds of cards and laptops from different vendors.
It looks promising that this chipset has been supported in Linux for a long time: [https://linux-hardware.org/?id=pci:1033-0194-1033-0194](https://linux-hardware.org/?id=pci:1033-0194-1033-0194)



I don't see anything special/custom with the card. It looks like an ordinary low-profile PCI-e x1 card with a SATA power connector, and should work in non-HP systems.
Good research; kinda weird that the op couldn't do it also.

---

### Post by Yellow Pasque on 2023-10-24
*Shrug* Vendors don't make it intuitive. It took me a while to dig that stuff up. And while I was googling, I saw plenty of complaints from Windows users about figuring out what driver to use for the card in question, at least on Win7 and older.

---

### Post by jimmyrus on 2023-10-25
> **Yellow Pasque said:**
> *Shrug* Vendors don't make it intuitive. It took me a while to dig that stuff up. And while I was googling, I saw plenty of complaints from Windows users about figuring out what driver to use for the card in question, at least on Win7 and older.
They often don't, but if you could find it you'd kinda figure the op had a better motive to dig it up instead of wanting someone else to do it

---


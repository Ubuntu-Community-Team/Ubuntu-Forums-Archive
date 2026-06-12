---
title: "[GPU] Question"
date: 2012-01-02
forum: Hardware
---

### Post by dak0 on 2012-01-02
Hello Ubuntu community, I`m having ASUS G-SURF365 Motherboard
 [http://www.asus.com/Motherboards/AMD_AM2/GSURF365/#overview](http://www.asus.com/Motherboards/AMD_AM2/GSURF365/#overview)
Can this Motherboard support this GPU 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1440108&Sku=M452-6452](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1440108&Sku=M452-6452)

Thanks, regards

---

### Post by MoreOrLess on 2012-01-02
It's a PCI-e 1.1 slot and a PCI-e 2.0 card. You should be able to use it with no issue (though I did have one PCI-e 1.x board with a ULI chipset that didn't like PCI-e 2.0 cards).

[http://en.wikipedia.org/wiki/Pci_express#History_and_revisions](http://en.wikipedia.org/wiki/Pci_express#History_and_revisions)
> PCIe 2.0 motherboard slots are fully backward compatible with PCIe v1.x cards. PCIe 2.0 cards are also generally backward compatible with PCIe 1.x motherboards, using the available bandwidth of PCI Express 1.1. Overall, graphic cards or motherboards designed for v2.0 will work with the other being v1.1 or v1.0a.

---

### Post by Sylos on 2012-01-02
Hello.

The asus site doesnt seem to specify whether the PCIe slots are v.1 or 2.0. If in doubt I would assume it to be v.1. 

As far as I am aware the two types are compatible. The PCIe 2.0 card should work in the v1.0 slot BUT it will only run at 1.0 standard. This could cause problems with using the card if the old 1.0 standard causes a bottle neck and reduces preformance. Idont know enough about these things to give you any ideas as to whether it will cause an issue. Maybe try contacting asus to confirm the standard of the slots before you buy.

Cheers

---

### Post by MoreOrLess on 2012-01-02
That mobo chipset was designed before pcie 2.0, so I'm pretty sure it's 1.1

The bandwidth difference shouldn't be an issue with a lower power card like the 6450.

---


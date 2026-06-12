---
title: "Multiple VIA VT6420 SATA controllers"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by xgravix on 2008-01-11
Hi,

The VIA VT6420 SATA RAID controller on my motherboard works well under ubuntu, so I bought an addon card with the same controller for more disks.

Unfortunately it does not work. I know the PCI card is seated correctly because the card also has an IDE controller, and I get one extra line "VT6421 IDE RAID controller" under lspci when the card is plugged in.

However, the SATA drives on the controller do not show up in /dev/sdc and /dev/sdd.

It is not possible to have two VT6420 SATA controllers at the same time? It only shows up once in lspci, and it is the one on the motherboard.

Thank you for any tips!

---

### Post by xgravix on 2008-01-11
In case anyone comes from google, the issue was that one of the controllers supported SATA II and one did not. So adding jumper pins for the drives on the older (but identically named) controller solved the problem.

---


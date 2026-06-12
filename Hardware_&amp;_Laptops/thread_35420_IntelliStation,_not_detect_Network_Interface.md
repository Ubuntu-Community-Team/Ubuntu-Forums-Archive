---
title: "IntelliStation, not detect Network Interface"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by persis on 2005-05-18
IntelliStation E Pro 6893-94U [change]

P3 600MHZ 512KB 128MB ECC 13.5GB HDD IDE PCI/ISA 4X4 40XCD MATROXG400 NT4

Just tried to install Ubuntu on the above system. installed fine but couldn't detect onboard network interface.

How do I go about setting up the mobo network to work with ubuntu so I can get online?

Thanks in advance.

---

### Post by Xerampelinae on 2005-05-18
Perhaps using lspci, you can see which ethernet controller it uses, and manually use modprobe to insert the correct module.  The modules are all in /lib/modules/*/kernel..

---


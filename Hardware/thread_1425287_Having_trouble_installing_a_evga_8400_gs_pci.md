---
title: "Having trouble installing a evga 8400 gs pci"
date: 2010-03-08
forum: Hardware
---

### Post by ghstridr on 2010-03-08
I'm installing this in a Dell Precision 690
The OS is Ubunutu 9.10 (all updates applied).
I've loaded the latest stable nvidia drivers (190.53) and it won't see it.
I looked at what the linux system thinks is in the slot and I get the following from lspci:
0c:02.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
I know this is the correct entry as in another machine I have a 6200 pci and it shows up at the same pci bus address (0c:02.0) and it works just fine.
So, I've got working drivers, but it recognizes the card as a PCI-E interface instead of something like:
0c:02.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---


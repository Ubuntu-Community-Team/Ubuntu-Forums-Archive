---
title: "Conexant ADSL PCI Modem - kernel config help"
date: 2004-12-21
forum: Hardware &amp; Laptops
---

### Post by fsman on 2004-12-21
I have a Conexant PCI ADSL modem and therefore need to compile my own drivers using the following guide ...

[http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html](http://patrick.spacesurfer.com/linux_conexant_pci_adsl.html)

Can someone confirm if the stock kernel has the following config/module as per section 2 of the guide.

ie..

Kernel configuration section     Description                                         .config Define              Status	
Networking options                  Asynchronous Transfer Mode (ATM)	CONFIG_ATM	On
Network device support           PPP (point-to-point protocol) support  CONFIG_PPP	On
Network device support           PPP over ATM                               CONFIG_PPPOATM	On
Processor type and features    Use register arguments               CONFIG_REGPARM	Off

Also. are the kernel sources on the ISO CD? if not its going to be difficult to download them if I can't get my modem working (a bit of chicken and the egg!).

thanks in advance

---


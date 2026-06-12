---
title: "FAXServer"
date: 2009-11-25
forum: Hardware
---

### Post by wjohnson2000 on 2009-11-25
I'm setting up a small fax server using Ubuntu 9.10. I have four PCI modems in the server, three of them are recognized and one isn't. The output from lspci -v shows that the ethernet controller and one of the modems are both using IRQ 21. I suspect this might be the problem. Is there a way to force the modem to use a different IRQ? Would moving the cards around help? There are no open PCI slots.

Thanks

---


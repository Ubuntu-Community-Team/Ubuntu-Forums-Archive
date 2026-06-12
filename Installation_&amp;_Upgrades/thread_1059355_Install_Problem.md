---
title: "Install Problem"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by edumega on 2009-02-03
When I click install the loading bar appears then an error continues appeaing:

I keep getting [ ***.******(number) ] ata2.00: status: { DRDY ERR }

Help!

---

### Post by Partyboi2 on 2009-02-03
Try booting using irqpoll as a boot option. At the main menu on the ubuntu live cd press F6 and add ```
irqpoll
``` to the end of the line after splash and press enter.

---


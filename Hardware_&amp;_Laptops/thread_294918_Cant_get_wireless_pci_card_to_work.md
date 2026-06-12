---
title: "Cant get wireless pci card to work"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by Streetwalker32 on 2006-11-07
The card is recognised in the device manager - but the power/link diodes is not flashing.

How do I get further ?




Ubuntu lamp + gnome desktop

---

### Post by michux on 2006-11-07
> **Streetwalker32 said:**
> The card is recognised in the device manager - but the power/link diodes is not flashing.

How do I get further ?

Ubuntu lamp + gnome desktop

Well it may be that there is no driver installed for your wireless card. Which card is it?

What happens if you type the following in the console:

```
iwlist eth1 scan
```?

If you have an unsupported card you may have to use Ndiswrapper (a Windows driver wrapper) to get it to work.

Anyway, just post more details and we'll try to help.

---

### Post by Streetwalker32 on 2006-11-07
eth1 Interface doesnt support scanning

---


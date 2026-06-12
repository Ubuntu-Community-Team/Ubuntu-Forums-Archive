---
title: "Problems with network on upgrading ACER 1692"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by tim987 on 2005-10-19
I was running Hoary for mounths with no problems (no acpi configured) and when updated to Breezy (changing sorces.list) my network conection doesn´t work anymore. 

The module (tg3) is loaded, but on boot or after booting the network doesn´t start (no dhcp works). Back to Hoary and everything works fine again. I think it´s a problem with /etc/iftab (or something similar, sorry I haven´t my laptop here now). Any idea?

Thx

---

### Post by civilwarlord on 2005-10-19
Have you checked /etc/network/interfaces?

---


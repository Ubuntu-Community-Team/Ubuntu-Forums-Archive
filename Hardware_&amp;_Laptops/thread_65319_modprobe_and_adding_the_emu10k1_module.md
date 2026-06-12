---
title: "modprobe and adding the emu10k1 module"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by Haegin on 2005-09-13
How do I add the emu10k1 module to my kernel as I can enter 
```
modprobe emu10k1
```
but when I restart it hasnt stored my changes. How do I make sure the emu10k1 module is loaded every time?

---

### Post by az on 2005-09-13
sudo gedit

and add it at the end of /etc/modules

---


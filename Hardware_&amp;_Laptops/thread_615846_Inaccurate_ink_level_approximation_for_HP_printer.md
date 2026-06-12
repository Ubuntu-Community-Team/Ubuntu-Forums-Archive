---
title: "Inaccurate ink level approximation for HP printer"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by srunni on 2007-11-17
Hi,

One of the new features in Gutsy I've noticed is the ink level approximation for (HP) printers. However, this approximation seems to be highly inaccurate - Ubuntu told me the ink is low, but I've printed 30-40 pages after that with no apparent sign that the ink is running out. Is this a known bug for Gutsy, and if so, can I turn off the message? It's really annoying seeing it pop up every time I print something.

Thanks in advance for the help!!

---

### Post by srunni on 2007-11-18
Anyone?

---

### Post by jongkind on 2007-11-18
I doubt whether the cause of this is related to Ubuntu: the cartridge chip measures the ink level, and it communicates this via Cups to Ubuntu. This means that it is a problem of an inaccurate ink measurement  the cartridge.

---


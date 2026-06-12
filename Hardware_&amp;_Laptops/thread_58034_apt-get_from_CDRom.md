---
title: "apt-get from CDRom"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by Dutch on 2005-08-18
Fucked up DSL after trying to install hylafax on  ttys2
Synaptic has died too

Is it posible to apt-get the DSL pakets from the Ubunto CDRom in a terminal ?
How ?

---

### Post by pmjdebruijn on 2005-08-18
Try uninstalling hylafax first...

If you already did that, If I'm not mistaken, apt-get using the CD-ROM by default (as primary source) for everything the CD-ROM contains. 

You can install seperate .deb files with dpkg -i foo.deb, but it's not recommended...

Regards,
Pascal de Bruijn

---


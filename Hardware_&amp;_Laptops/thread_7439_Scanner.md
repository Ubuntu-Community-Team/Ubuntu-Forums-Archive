---
title: "Scanner"
date: 2004-12-07
forum: Hardware &amp; Laptops
---

### Post by nono on 2004-12-07
Hallo !
I remplace my Mandrake 10.0 by ubuntu ,my scanner and k3b no work wicth
how  I do ?
sorry for my english i francophone!!!

---

### Post by broseman on 2004-12-09
Welcome nono!

--> Scanner

Please post vendor and model of your scanner.
You probably will have to edit the file /etc/sane.d/dll.conf
Look for your scanner in the list and remove the #.
Than try start xsane, maybe sudo xsane.

--> k3b

Did you use synaptic for installing k3b? If not, give it a try.

Greetings,

 broseman

---


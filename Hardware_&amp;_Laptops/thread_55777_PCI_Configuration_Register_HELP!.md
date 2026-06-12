---
title: "PCI Configuration Register HELP!"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by Fluffz on 2005-08-10
Hi!

i need to change 1 register in PCI Register.

[www.h-oda.com](www.h-oda.com) supported a tool WPCREDIT where i easy change 
Register 50xFC to FF ! 
FF rise IOQueue to max so i get full 1900MB/s ramtransferrate.

Now i only got 1100 MB/s so i also will boost up in ubuntu

1. i know cmd lspci -v but i dont see the register 50xFC at all!
how i can see changes using lspci?

2. i noticed there is a nice tool called setpci.
am i right change Register in setpci to 50xFF syntax should be 
setpci -v -H1 -s 0:0:0 0x50=0xFF ?? i donno if this is correct

3. how i get this change on startup ?

ty fluffz

---

### Post by Fluffz on 2005-08-10
Solved ty

---


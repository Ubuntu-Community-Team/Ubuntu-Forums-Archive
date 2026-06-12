---
title: "Installation stop at loading kernal"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by creepmaster on 2006-10-28
Firstly, sorry for my english.

Asus notebook A6k
-Turion64 MT34 1.8G
-Hdd 100GB 20 for winxp, 60 for data and 20 unpartitioned
-ram 512
-nVidia Geforce GO7300

-Ubuntu edgy amd64 alt
-Ubuntu dapper amd64 live

I tried them both and they stuck at the same place,load kernal before the 2nd ubuntu logo(just 2 lines after press enter).

I tried12x and 4x write speed and I burned image correctly(not data burning).

They can boot but can't goon.

please, I need your help

---

### Post by velozoom on 2006-10-28
same problem with my dv9000 

try adding the following boot parameters (press f6 when the live CD gets to the options menu)

-noapic -nolapic

this works for the live CD, installed OS, and booting into command line only.  

I would love to know how to NOT have to do this every time.....

---


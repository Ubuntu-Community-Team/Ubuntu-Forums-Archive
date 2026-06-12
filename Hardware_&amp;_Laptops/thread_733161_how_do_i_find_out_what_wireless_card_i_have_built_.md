---
title: "how do i find out what wireless card i have built in"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by laurencemulchrone on 2008-03-23
i have a toshiba 4600 running xubuntu gutsy. 

is their a way of finding what chipset/brand my built in  wireless adapter is. i.e thru terminal.

i need to know so i can use ndis wrapper in damn small linux

i cant find the info in the net anywhere!

---

### Post by lloyd_b on 2008-03-23
> **laurencemulchrone said:**
> i have a toshiba 4600 running xubuntu gutsy. 

is their a way of finding what chipset/brand my built in  wireless adapter is. i.e thru terminal.

i need to know so i can use ndis wrapper in damn small linux

i cant find the info in the net anywhere!

In a terminal window, run the "lspci" or "lshw | more" commands.  The wireless adapter should show on one (or both) of these.

Lloyd B.

---


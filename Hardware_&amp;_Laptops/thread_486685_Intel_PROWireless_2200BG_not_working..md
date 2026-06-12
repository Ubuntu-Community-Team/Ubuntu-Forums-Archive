---
title: "Intel PRO/Wireless 2200BG not working."
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by madmax2007 on 2007-06-28
Running Ubuntu from CD to test before installing for good on a Sony Laptop. The wireless connection will not work. It is an Intel PRO/Wireless 2200BG. 
I am wondering if the demo is the problem and it should work once it is installed?

---

### Post by zgornel on 2007-06-28
> **madmax2007 said:**
> Running Ubuntu from CD to test before installing for good on a Sony Laptop. The wireless connection will not work. It is an Intel PRO/Wireless 2200BG. 
I am wondering if the demo is the problem and it should work once it is installed?
Try posting a ```
dmesg
```. Some answers might be there.

---

### Post by davecambs on 2007-06-28
it will work when you install, it sometimes needs a bit of tinkering, I use ndiswrappper to get mine working - you can download this from synaptic or the add package manager, just search on here for threads on how to do the install

---

### Post by whayong on 2007-06-28
Mine works.  I didn't get to try it in the install CD because I already had Ubuntu installed when I switched out the  wireless cards.  Try to see if you see "eth1" when entering iwconfig in terminal.

---


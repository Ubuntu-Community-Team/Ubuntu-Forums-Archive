---
title: "No multitouch on EEE 1000 HE and kernel 2.6.28.7"
date: 2009-03-15
forum: Hardware
---

### Post by ygingras on 2009-03-15
Hi, I'm running 8.10 on a EEE 1000 HE.  If I run on the stock 2.6.27.3 kernel, I have multi-touch out of the box.  However, wifi does not work with 2.6.27.3 so I built a 2.6.28.7 kernel by hand.  Wifi now works but I lost multi-touch.  Anyone knows if Ubuntu includes patches that are not merged in kernel.org that would be critical for multi-touch to work?  I did a make oldconfig with the the Ubuntu kernel config before compiling.  Thanks in advance for any hints on how to solve this problem.

---

### Post by ygingras on 2009-03-16
I still don't know how to get the multitouch to work on 2.6.28 but I can get the wifi to work on 2.6.27-11 by installing compat-wireless-2009-03-15.

---


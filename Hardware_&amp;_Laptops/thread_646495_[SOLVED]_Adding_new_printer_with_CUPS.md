---
title: "[SOLVED] Adding new printer with CUPS"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by johnleonard on 2007-12-21
I'm having problems adding a local printer (Lexmark z11, parallel port) using both the Xubuntu Printing wizard and also CUPS.

Using CUPS when I truy to print a test page I am getting the following error

> recoverable: Network host 'localhost' is busy; will retry in 15 seconds..."

Can anyone tell me where I am going wrong?

---

### Post by johnleonard on 2007-12-21
Solved - I set the device to be epson:/dev/lp0 and it worked.

---


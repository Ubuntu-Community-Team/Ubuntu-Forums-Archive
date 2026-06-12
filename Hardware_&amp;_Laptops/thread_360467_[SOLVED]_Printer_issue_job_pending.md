---
title: "[SOLVED] Printer issue: job pending"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by jesuisbenjamin on 2007-02-13
Hello,

I have two printers connected to my PC:
1- HP deskjet 510, connected via LPT1
2- Lexmark Z35, connected via USB

Originally, after installation i was able to print normally (although these printers are old and somehow rusty). At some point when printing, the jobs hang on. On the printer itself, the status remains as "ready" and not "busy". This occurs with both printers, although connections differ, i concluded something is happening within the software.
I un-installed the printers, booted and re-installed them, booted again and the problem occurred anew, the issue happened before i ran the updates and continued thereafter.

What can one do with this issue?

Thanks in advance.

---

### Post by tgalati4 on 2007-02-20
CUPS my friend.  It's time to lift the hood and take peek at what is going on.

What do you see as the printer status? In Firefox:  localhost:/631

Share with us some interesting error messages from /var/log/cups

---


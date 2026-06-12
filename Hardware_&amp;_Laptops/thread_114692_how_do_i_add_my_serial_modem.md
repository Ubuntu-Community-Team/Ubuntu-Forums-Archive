---
title: "how do i add my serial modem?"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by maduranga on 2006-01-09
i have a modem wich connected through the serial prot and can be work without 
any driver installation. It is successfully working on windows xp. How do i add this modem on ubuntu and get connected?

---

### Post by endangst on 2006-01-09
Try sudo pppconfig

After going through that, to make your modem connect do this:

sudo pon provider

Where "provider" is the name that you gave to your connection.

I hope this helps.  It worked for me setting up my external modem which is a cell phone. ;)

---

### Post by maduranga on 2006-01-13
:D thx a lot.. it works............

---


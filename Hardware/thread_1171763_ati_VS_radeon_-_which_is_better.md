---
title: "ati VS radeon - which is better?"
date: 2009-05-27
forum: Hardware
---

### Post by bobnutfield on 2009-05-27
Hello everyone,

I am one of those poor souls who lost their prop. drivers for my Express Radeon X1250 in my Toshiba laptop.  I just upgraded to Jaunty (knowing that I would not have fglrx anymore).  But, Jaunty loaded the "ati" driver as default.  I know there is also a "radeon" open source driver.  I am not getting very good performance from the current ati driver and was wondering if anyone has tried the "radeon" driver.  What is the difference?

Thanks for any replies.

---

### Post by lvu on 2009-07-22
Ati and radeon drivers are essentially the same in your case. Ati is just a wrapper which loads an appropriate driver for your card - it may be radeon, rage128, etc.

You may try radeonhd driver.

---


---
title: "Ubuntu 12.04 Battery drains overnight in hibernation mode"
date: 2014-08-03
forum: Hardware
---

### Post by Dawood_Shahid on 2014-08-03
Isn't it supposed to drain the battery at the minimum? Sleep causes my Wifi to be hard blocked. But that isn't the case here. I want some solutions for my hibernation problem. Plus my laptop stays heated during hibernation.....

---

### Post by weatherman2 on 2014-08-03
It sounds like your laptop is not in fact hibernating.  If it is still running and not hibernated, naturally it will drain the battery in short order.

Hibernation problems are common in Linux unfortunately.  This is one reason hibernation is disabled by default in Ubuntu nowadays. Depending your laptop hardware, there may be tricks to make it work correctly.  I have tried to fix hibernation on several laptops in Ubuntu sometimes with success often not.  Fortunately, standby almost always works or can be made to work fairly easily, although that does drain the battery gradually.

---

### Post by Dawood_Shahid on 2014-08-04
Is there any way to make it hibernate?

---

### Post by Vladlenin5000 on 2014-08-04
> **Dawood_Shahid said:**
> Is there any way to make it hibernate?

It depends on your hardware and enough space allocated to the swap partition which should be at least the same as your RAM.

---


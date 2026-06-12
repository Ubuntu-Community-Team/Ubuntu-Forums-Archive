---
title: "Computer turns off suddenly"
date: 2008-12-17
forum: Hardware
---

### Post by Jayhawker on 2008-12-17
Please, 

Can you tell me the reason my pc, a dual core, turns off itself after few minutes if I see or listen to some media and after a few longer  browsing websites. Very nagging indeed!

How can I solve it?

---

### Post by lykwydchykyn on 2008-12-17
Does the hardware shut completely down?  Sounds like a heat issue, though it could be a faulty PSU or Motherboard.

---

### Post by Kevbert on 2008-12-17
Do you get an error in /var/log/kern.log when the PC shuts down after a short while ? It's possible that you may also need to look at kern.log.0. You should be able to track the error via the time stamp if something occurs just before the shutdown.
As lykwydchykyn suggests it could be a heat problem.  May be worth running memtest from the boot menu.
Does it occur after x minutes and is repeatable ?

---

### Post by Jayhawker on 2008-12-17
> **Kevbert said:**
> Do you get an error in /var/log/kern.log when the PC shuts down after a short while ? It's possible that you may also need to look at kern.log.0. You should be able to track the error via the time stamp if something occurs just before the shutdown.
As lykwydchykyn suggests it could be a heat problem.  May be worth running memtest from the boot menu.
Does it occur after x minutes and is repeatable ?

Yes, it occurs always after any activity I said above, but it keeps running almost stable if I don't do anything, when idle, except every now and then.

---


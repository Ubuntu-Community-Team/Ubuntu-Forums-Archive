---
title: "X Randomly Shuts Down"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Afoot on 2008-01-28
And I get flooded my messages saying something like "over-current change on usb port 2". This is a known hardware problem on this computer, however, is there any way to make it NOT restart X everytime that happens? On windows I just get an alert message in the system tray which can be disabled.

---

### Post by frodon on 2008-01-28
Often with such problems a BIOS update is the only way to to get a chance to fix it, however BIOS updates are something serious which is often a last chance solution.

Did you check if your laptop constructor has released a BIOS update to fix this ?

---

### Post by Afoot on 2008-01-28
I don't think it can be fixed with a BIOS update, I've tried that already. But is it possible to not allow X to shut down because of the problem?

---

### Post by Afoot on 2008-01-28
Bump

---

### Post by Afoot on 2008-01-29
Surely there must be some way to prevent this from happening? I'd hate to have to install windows on it...

---

### Post by frodon on 2008-01-29
Could you paste the corresponding error log from "syslog", "message" and "kern.log" logs, you should find them quickly using the system log viewer.
First we would need to get what exactly is sending the xserver restart command or what is making it crashing.

---

### Post by Afoot on 2008-01-29
> **frodon said:**
> Could you paste the corresponding error log from "syslog", "message" and "kern.log" logs, you should find them quickly using the system log viewer.
First we would need to get what exactly is sending the xserver restart command or what is making it crashing.
Syslog (it was too big to post the whole thing):
[http://rafb.net/p/NdpRTN26.html](http://rafb.net/p/NdpRTN26.html)
Messages:
[http://rafb.net/p/k0tFvs84.html](http://rafb.net/p/k0tFvs84.html)
Kern (too big as well):
[http://rafb.net/p/wryBgj88.html](http://rafb.net/p/wryBgj88.html)

---

### Post by Afoot on 2008-01-30
Bump.

---

### Post by Afoot on 2008-01-31
Bump...

---

### Post by frodon on 2008-01-31
Afoot you should also post the exact name of your computer especially the name of the hardware which is known to create the problem. Your are more likely to get good help from users running ubuntu on the same hardware and i'm sure there's some.

---


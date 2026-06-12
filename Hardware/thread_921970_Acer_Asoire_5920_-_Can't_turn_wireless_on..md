---
title: "Acer Asoire 5920 - Can't turn wireless on."
date: 2008-09-16
forum: Hardware
---

### Post by Envergure on 2008-09-16
After turning my wireless off i can't turn it on again without rebooting.  I have an Acer Aspire 5920, and i installed a different driver which was supposed to make the wireless LED work.  Any help?

To turn it off i just press a button on one side of the keyboard.  After that, if i right-click the network tray icon "enable wireless" is greyed out.

---

### Post by Dao984 on 2008-09-19
run in terminal:

sudo ifconfig wlan0 up

Bun i dont' know how turn on wi-fi from wireless

---

### Post by Envergure on 2008-09-20
```
SIOCSIFFLAGS: No such device
```

---

### Post by Dao984 on 2008-09-21
u can try:

```
sudo apt-get install linux-backports-modules-hardy
```

---

### Post by Envergure on 2008-09-23
No.  Is it likely to magically start working once i have Intrepid installed?

---

### Post by Envergure on 2008-09-26
I've come up with a temporary workaround:  I can turn it on by hitting the button, suspending my computer and waking it up again.

---

### Post by tfm_copycat on 2008-11-15
> **Envergure said:**
> I've come up with a temporary workaround:  I can turn it on by hitting the button, suspending my computer and waking it up again.

Or rebooting into windows to turn wifi on. Isn't there a workaround? I couldn't care less about the led (in fact, I prefer that it doesn't blink at all) but the functionality of the switch (which worked flawlessly in HH) now is gone.

No solutions so far??

---

### Post by zloyzenka on 2009-03-12
have same problem with same laptop.

---


---
title: "Gutsy wireless won't reconnect after going to sleep"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Barleyman on 2007-10-24
I am running Gutsy on Thinkpad T61 with Intel 4965 AGN wireless card.

Everything works fine, but if laptop goes into sleep mode, network manager is unable to reconnect to wireless network unless laptop is rebooted.

Any help in troubleshooting would be appreciated.

ps. I am running 32bit gutsy

---

### Post by Barleyman on 2007-10-25
Any help with troubleshooting this?

---

### Post by Arthur Archnix on 2008-02-25
I'm looking for the same answer. I do know that this forces a reconnect without rebooting.
```
sudo ifdown -a
sudo ifup eth1
```

---


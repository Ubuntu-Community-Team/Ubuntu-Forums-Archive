---
title: "Help - How to get my laptop's WLAN switch work"
date: 2009-03-02
forum: Hardware
---

### Post by ProNux on 2009-03-02
Hi there,

I am running Hardy on my Acer 4710 with a built in Intel 3945abg WLAN.  It has an external switch that works well in Windows.  I have searched regarding this one but can't find one.  Other buttons like Internet browser and Email works.  Any help?

By the way, the switch works on Intrepid - one way only - that is, turning the the WLAN OFF. But it cannot turn it ON.  I have to restart networking to turn it on.  And at Interpid, If I turn the WLAN off, even my external (USB) WLAN also turns off, which should not be.

---

### Post by ddrichardson on 2009-03-03
I don't know the exact keycodes, so you might need some experimenting but these codes work on the Acer Aspire One so might set you in the right direction:
```
/usr/bin/setkeycodes e055 159[FONT=monospace]
[/FONT]/usr/bin/setkeycodes e056 158
```
Note that if you want this automatically at boot then theres a guide to /etc/rc.d/local [here]("https://help.ubuntu.com/community/RcLocalHowto").

---

### Post by ProNux on 2009-03-04
> **ddrichardson said:**
> I don't know the exact keycodes, so you might need some experimenting but these codes work on the Acer Aspire One so might set you in the right direction:
```
/usr/bin/setkeycodes e055 159[FONT=monospace]
[/FONT]/usr/bin/setkeycodes e056 158
```
Note that if you want this automatically at boot then theres a guide to /etc/rc.d/local [here]("https://help.ubuntu.com/community/RcLocalHowto").

Thanks bro.  Gotta try it out later when I'm home.

---


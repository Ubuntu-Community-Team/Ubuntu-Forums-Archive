---
title: "pcmcia or wifi problem?"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by fmarcia on 2005-08-31
Hi all,

I've got a hp omnibook vt6200 and I'm trying to connect to my wifi router via a d-link dwl-g650 pc card... no way :-(

In the device manager, I can see the pc card but its light never turns on... and, of course, no ip address, no gateway...

Thanks for your help.

---

### Post by gravestone on 2005-09-01
Sounds like a PCMCIA problem, because when I insert my card, the light goes on. Open a terminal and type :   sudo cardctl ident

It should give you some information on the currently inserted card. If it says no info, it's a pcmcia problem. If it comes back with the info, it should read dwl card etc. I used the atheros driver, and it runs this card on ath0.

---

### Post by fmarcia on 2005-09-02
Resolved: it's a pcmcia problem. My card is not supported natively. I must use ndiswrapper.

Franck.

---


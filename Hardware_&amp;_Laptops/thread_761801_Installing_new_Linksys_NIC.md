---
title: "Installing new Linksys NIC?"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by garyvdm on 2008-04-21
Hi 

I just added a Linksys LNE100TX Nic to my computer. If I type ifconfig, it does not appear. How do I get ubuntu to install it.

I am using xubuntu 7.10 gusty.

Gary

---

### Post by stchman on 2008-04-21
> **garyvdm said:**
> Hi 

I just added a Linksys LNE100TX Nic to my computer. If I type ifconfig, it does not appear. How do I get ubuntu to install it.

I am using xubuntu 7.10 gusty.

Gary

Supposedly that card is supported by the TULIP driver and that is in the 2.6.xx-xx kernel.

Give us an lspci output here.  Did you try ifconfig -a which gives more information?

---

### Post by garyvdm on 2008-04-21
Thank you for the reply.

It starting working after doing a software update and restart.

Sorry if I wasted your time.

Gary

---


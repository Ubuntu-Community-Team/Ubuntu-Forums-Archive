---
title: "ATI TV wonder 650"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by k3nz0 on 2006-12-16
i have an ATI TV Wonder 650 and I was wondering if anyone got one to work.
I can't even get ubuntu to detect it.  well it detects it, but  doesn't look like it knows what to do with it.
when I do a "lspci" it comes back with;
Multimedia controller: ATI Technology Inc Unknown device 4d50.
I googled for ever and i can't find anything or anyone who's ran into this card.
I'm trying to setup a Mythtv box.  So far this is the only part that doesn't work.
I'm about to get a different card, but i would rather not.

thanks.

---

### Post by superm1 on 2006-12-16
> **k3nz0 said:**
> i have an ATI TV Wonder 650 and I was wondering if anyone got one to work.
I can't even get ubuntu to detect it.  well it detects it, but  doesn't look like it knows what to do with it.
when I do a "lspci" it comes back with;
Multimedia controller: ATI Technology Inc Unknown device 4d50.
I googled for ever and i can't find anything or anyone who's ran into this card.
I'm trying to setup a Mythtv box.  So far this is the only part that doesn't work.
I'm about to get a different card, but i would rather not.

thanks.

I don't think this device is supported in linux as of yet.  You should check with the mythtv mailing list to double check, but a quick google search indicates that there are no linux drivers for the card.

---

### Post by k3nz0 on 2006-12-18
> **superm1 said:**
> I don't think this device is supported in linux as of yet.  You should check with the mythtv mailing list to double check, but a quick google search indicates that there are no linux drivers for the card.

I didn't think so.  I googled for like 3 days on this that's why I finally posted the question.
I gave up on it. I'm getting a different card PVR150 or something.

---

### Post by superm1 on 2006-12-18
> **k3nz0 said:**
> I didn't think so.  I googled for like 3 days on this that's why I finally posted the question.
I gave up on it. I'm getting a different card PVR150 or something.
Good choice for a card :)
I've got a howto for the hauppauge pvr-series cards here too, so once you get it, shouldn't be too bad to set up:
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

---

### Post by Neuralgia on 2007-04-22
Same here.

I bought this card because of great CNET reviews.

It also included a free remote.

Shortly after, started playing with Linux.

The ONLY thing missing for me is TV :( 

Very weird, that such a card with even great reviews has no Linux drivers. CNET mentions is the best card on its type.

PS:

> $ lspci
04:00.0 Multimedia Controller: ATI Technologies Inc Unknown Device 4d50

---


---
title: "When I restart my ubuntu it's changes the ID of my cards (GPUs)"
date: 2019-10-26
forum: Hardware
---

### Post by nestdrs on 2019-10-26
Hi all, I have a problem, i have installa three Ati RX580 in my ubuntu 18.04 and my motherboard have one more inserted .
when i start my device sometime ubuntu change de ID de card (GPU) of motherboard by the card one RX580 and y don't want change the devices, I want to the card0 always be the motherboard GPU and the rest of card always same nunmber,
Can somebody help to me?

---

### Post by nestdrs on 2019-10-29
Hi, nobody can help my?... :cry:

---

### Post by #&amp;thj^% on 2019-10-29
> **nestdrs said:**
> Hi all, I have a problem, i have installa three Ati RX580 in my ubuntu 18.04 and my motherboard have one more inserted .
when i start my device sometime ubuntu change de ID de card (GPU) of motherboard by the card one RX580 and y don't want change the devices, I want to the card0 always be the motherboard GPU and the rest of card always same nunmber,
Can somebody help to me?
Your not giving enough information for us to help you. ;) When a request for help is asked give us something to go on and not so vague.
How did you configure them? (This includes everything you have done up to now)
Also add this please:
```
cat /etc/X11/xorg.conf
```
And are you using any related PPA's for this.

---

### Post by nestdrs on 2019-10-29
Thanks for you answer, I don´t know else I can say. I installed the driver of AMD, the free driver in a Ubuntu 18.04, all card are configuerd in the path, /sys/class/drm/
in this path are card0, card1, card2, cardx..... (card0 = Motherboard, card1 = RX580-1, card2 = RX580-2 and card3 = RX580-3) 
when I restart to pc, the card0 change of name at card1 and card1 change at card0.
if I want to the cards it in the instead, i have to restar the PC until the card are left in place, several times


I need thar because I want to make undervolt and I need know the name of each card
sorry my poor english :icon_frown:

---


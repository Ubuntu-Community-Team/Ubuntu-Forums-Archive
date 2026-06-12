---
title: "Latitude laptop"
date: 2008-06-11
forum: Hardware
---

### Post by woztron on 2008-06-11
Hey, just hoping someone has had one of these old things.

Its a Latitude c510, supposedly has built in wireless, at least i can't find a removable wireless card anywhere inside the thing (it has a modem in the pcmcia slot).  I know it works, last week when it arrived from ebay it worked in xp.  First thing i did was an xubuntu alternate install without thinking to back up the current drivers (i was excited :) ).  Thats where it all unravelled.

My gf uses the laptop for work so it has windows on it for the moment until i can make ubuntu work perfectly she won't make the change.

I ran the lspci command and though i don't the output i know it led  me to believe i needed the acx111 (its a texas instruments chip, don't know the precise chipset) driver which works natively in linux.  I got it to connect once to my WPA network, since then nada.  

When i reverted to xp, i can't get it to work again either, can't track down the correct driver.

So, what i'm asking is has anyone got this working or got ideas for me to try?  

Even just the chipset of the wireless would be great!!!

---

### Post by apt-e on 2008-11-28
Hi 
I had the same problem with my D505.  After enabling the Proprietary drivers in software sources a B43xxx driver appeared.

I installed it, and now my laptop is working fine over the wireless.

I hope this helps.

APT-E

---


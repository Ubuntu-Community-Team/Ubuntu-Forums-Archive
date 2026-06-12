---
title: "Hard Drive errors on SSD  and new hard drive"
date: 2013-01-19
forum: Hardware
---

### Post by Carro on 2013-01-19
hi guys ,
i have tried ubuntu 12.10 
 i have issues on my thinkpad t61
i was using 250GB Gskil SSD and started getting read errors ( the drive worked fine with windows for over a year )
thought maybe the drive is going bad ( googled read error etc ) ..installed on new samsumg 320 gb drive and same issues .. started getting read errors
i did google those and seems there might be old issues with this .. now honestly i dont understand a whole lot of hdparams etc but can someone please help me 
i would like to figure out if there is really something wrong with the disk or can i tune some parameters

i have installed smartcontrol tools 

I installed XP on a smaller partition which works fine 

thanx all PLEASE help if you can.

---

### Post by oldfred on 2013-01-19
Welcome to the forums.

XP may not work with SSD. Did you change BIOS to AHCI and then install the AHCI driver with your XP install. I stopped booting XP (as promised for about 5 years :) ) when I added my SSD as it is not easy to add AHCI drivers after the fact.

Trim does not work unless AHCI is on in BIOS.

---


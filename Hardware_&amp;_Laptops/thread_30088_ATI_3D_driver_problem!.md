---
title: "ATI 3D driver problem!"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by Sonic-NKT on 2005-04-27
Hi,
tried everything i know to get this fglrx driver working (with 3D)... no luck.
i did everything exactly the same like in this tutorials on this page.
(i just used the fglrx package on the ubuntu servers until now, didnt compiled my own driver with the rpm from ati)
and now here is the detailed problem:
when i use the fglrx driver instead of the ati (in the xorg conf) and also load the module dri then the xserver wont start and the whole system crashes.. no jumping to other consoles or something like that. just dead and all i can do is press the reset switch.
but when i dont load this dri thing the xserver starts like normal, but i dont have hardware acceleration for 3D.
can someone help me. dont know what do to anymore.

PS: i also noticed that linux says i have 2 ATI graphic cards in my PC both the same, but the second one is called secondary.

now some info on my pc:
ATI Radeon 9200 128MB DDR
AMD Athlon XP 2400+
Ubuntu Linux 5.04, no kernel updates or anything.

thanks bye

---

### Post by Burgundavia on 2005-04-27
Ok, couple of things:

1. I assume you 9200 is a dual head card. That is what the second "card" is

2. If you have an nforce2 chipset board you need to look at [www.ubuntu.com/wiki/BinaryDriverHowto](www.ubuntu.com/wiki/BinaryDriverHowto) again, look at the bottom of the ATI section regarding the AGPpart thing.

3. As for adding DRI issue, that is odd.

Hopefully this solves your issue,

Corey

---

### Post by alastair on 2005-04-27
I think "secondary" just means you have 2 outputs on the card. 

If you can, for a fglrx boot, post :

/etc/X11/xorg.conf

and the X log :

/var/log/Xorg.0.log

(check the log is for the FGL driver - you might need the Xorg.0.log.old)

---

### Post by Sonic-NKT on 2005-04-27
i dont have a nforce chipset, some sis thing
ok will change it to fglrx again later and then post you the config and the log.

---


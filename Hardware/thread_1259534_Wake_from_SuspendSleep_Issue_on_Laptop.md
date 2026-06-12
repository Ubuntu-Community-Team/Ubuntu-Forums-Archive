---
title: "Wake from Suspend/Sleep Issue on Laptop"
date: 2009-09-06
forum: Hardware
---

### Post by fjanoos on 2009-09-06
Hi,

I have Ubuntu 9.04 (with Gnome) installed through Wubi running on my HP ProBook Laptop (Intel(R) Core(TM)2 Duo CPU T9600  @ 2.80GHz, 4GB Ram, ATI 512MB HD 4300).

I am having a problem of inconsistent behavior waking from the Suspend mode - if I startup my laptop within a few minutes (typically < 2) of suspending - it will wake up fine. However, if I wake it up after that - it may or may not wake up. Sometimes it will just show a blank screen with the mouse pointer - but it wont' respond to mouse or kbd actions - and the hdd will start spinning every so often.

This is esp. true if i suspend my m/c over night - it will absolutely not wake up the next morning. 

Any suggestions ?

Thanks,
-firdaus

---

### Post by fjanoos on 2009-09-06
Also, when I try to hibernate my computer - I get the following error message:

Sep  6 14:13:49 bourbaki kernel: [ 1675.540182] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xf t4
Sep  6 14:13:49 bourbaki kernel: [ 1675.540183] ata2: irq_stat 0x40000001
Sep  6 14:13:49 bourbaki kernel: [ 1675.540187] ata2: hard resetting link
Sep  6 14:13:49 bourbaki kernel: [ 1675.660646] PM: writing image.
Sep  6 14:13:49 bourbaki kernel: [ 1675.660660] PM: Free swap pages: 0
Sep  6 14:13:49 bourbaki kernel: [ 1675.660661] PM: Not enough free swap
Sep  6 14:13:49 bourbaki kernel: [ 1675.700590] Restarting tasks ... done.

and it wakes back up.

Is this related ?
-fj

---

### Post by nmaster on 2009-09-06
i have the same problem with suspend, but my hibernate works perfectly.  

since jaunty is so fast to boot up and shut down it hasn't been a huge bother, but it would definitely be nice to see a fix.

EDIT: sorry i didn't see that you were using Wubi.  Hibernate doesn't work for wubi.  i think suspend is supposed to work tho...

---


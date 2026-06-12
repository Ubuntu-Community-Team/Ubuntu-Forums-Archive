---
title: "[SOLVED] RAM recognition???"
date: 2009-01-03
forum: Hardware
---

### Post by Skripka on 2009-01-03
So today I finally received my 4 new DIMMs of memory from NewEgg.

Similar to this, only 2X1 GB DIMMs, instead of 2GB--same timings/latency

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820144120](http://www.newegg.com/Product/Product.aspx?Item=N82E16820144120)


BUT-2 strange things:

Mainly, my BIOS _only posts me having 3.2GB of memory instead of 4 GB_.  I plug in 2 DIMMs at a time-and I'm able to get each pair to post as 2GB....BUT all 4 together will ONLY post as 3.2GB :confused::confused: .  See my sig for specs-my K9N Neo has a max of 4GB memory according to the manual.  Tried resetting the CMOS jumper-no joy.

The other notable unintended side effect of my memory upgrade-was that my wireless card no longer works in *buntu.  Tried all my wizardry, and the card refuses to activate or respond to modprobe.  Card worked fine until the memory swap.  Card still works over on my WinXP install fine.  This I don't care about too much-as I said fck it, and bought a CAT6 cable (all WorstBuy had).

---

### Post by sendblink23 on 2009-01-03
Random reply question..  does your Windows.. recognize 4gb RAM .. with both inside ??  or  is it still say 3.2gb Ram ?

---

### Post by Skripka on 2009-01-03
> **sendblink23 said:**
> Random reply question..  does your Windows.. recognize 4gb RAM .. with both inside ??  or  is it still say 3.2gb Ram ?


Any and all help is appreciated :)

Windows reports:

"3.25 GB RAM
Physical Address Extension"

This is WinXP SP3 32bit if it matters.

FWIW-BIOS reports 3328MB memory.

---

### Post by Skripka on 2009-01-03
Well, I went and did the one thing I forgot to do-try a BIOS update and flash...and what do ya know--there's where the memory was hiding 
.

D'oh!

---


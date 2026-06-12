---
title: "Win7 not detected"
date: 2013-04-10
forum: Hardware
---

### Post by Jacobsen0 on 2013-04-10
I am doing a dual boot installation but my Win7 is not detected.. it does not even show the partitions on my SSD
it just says it is all unallocated, but there should be 50gb unallocated and rest used by windows7 out of 256gb
got no problems with win7.

My hardware spec is:

Motherboard:   Asus P9X79
Ram:              16gb corsair dominator
CPU:               I7-3820
SSD:              Samsung 840 Pro 256gb
HDD:              2x WD 1Tb
graphics card:  Nvidia GTX 680

I know all the parts are quite new.. can that be the reason ?

I seem to always have problems with installing Ubuntu :(  but I usually get a new computer once a year with newest hardware parts
last time it was my graphics card, I tried everything I could to install ubuntu! even posted here in the forums.. after weeks of trying I gave up..
so I was like *ah well..I get a new computer anyway in a few months* ... and now I cant AGAIN! :(

---

### Post by blackbird34 on 2013-04-11
Do you mean you can't boot into it?
Have you tried ```
sudo update-grub
```
It should update the bootloader (the program that gives you -or should give you- the choice between Ubuntu and Windows at startup). Are both systems on the SSD?

If you want to get used to Ubuntu, you could always just use a cheaper, older computer. It would be almost guaranteed to install fine.

---


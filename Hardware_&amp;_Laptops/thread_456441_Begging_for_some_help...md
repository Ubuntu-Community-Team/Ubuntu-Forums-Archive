---
title: "Begging for some help.."
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by termi on 2007-05-27
Hey, and thanks for reading.

Im new to linux and so far my experience has been worse then most.

i installed ubuntu, and tried to download nvidia drivers. i ended up using edgy, a program that installed all the drivers on its own. That went wery well, the first time...

i had to format the disks to change the size of the disk and install ubuntu again, when it happened...

i installed the nvidia drivers, and the computer reboots.

BOOM in my face it hits. The blue screen of death. Plug and Play have detected an error and will shut down windows to prevent damage.... 

i reboot and start ubuntu again. the ubuntu loader shows, and the nvidia logo, and the screen makes some weird glitches and it goes black... 

after praying for it to go further i relog, and same things happend, in windows and linux. I try windows inatall cd. it gives bluescreen before i get to the install/format disk screen. Opensuse install cd locks compleetly when it checks for harddisks, and ubuntu is all lost.

all i got to work with is ubuntu command line in recovery mode. windows safe mode crash before it has loaded all the drivers. all lead to BSOD...


so i beg you any ideas?
-----------------------------

Dell XPS laptop, M1710 
2.16ghz dual 2core
NVIDIA GeForce Go 9750 GTX
2gb memory,
dual boot XP and ubuntu 7.04 Fiery installed.
:(

---

### Post by termi on 2007-05-27
if you say bricked i will cry...

how can normal drivers kill a graphic card?

---

### Post by DerHesse on 2007-05-27
Are you sure your formatting the disk was ok? Was ubuntu working without the nvidia- installation? 
Why should windows be affected by a device driver in linux? Makes no sense to me.

...or it is just a co-incidence and your graphics-chip is broken.

Try a live-cd to find out.

---

### Post by ryanVickers on 2007-05-27
Strange.  The only thing that I can slightly relate to like this is I had really messed up the permissions for my / directory and nothing could work - not even the cd!  It was wierd because it shouldn't touch the harddrive without permission.  I fixed it eventually, but maybe try re-formatting everything from the terminal and then try to reinstall (if you don't have any important data that could be lost.  If that's the case, copy it off before this).

As for why windows doesn't work, I think that wil alway be a mystery...  Did you eat pizza for supper one day and then wear pants some time in the next 3.72 hours :p


I hope you get everything working ok again - linux is not normally like this, don't let it turn you off!

---

### Post by termi on 2007-05-28
how do i format the whole disk from terminal? i got nothing that cant be lost i want my pc back!

---

### Post by ramjet_1953 on 2007-05-28
Just boot from the LiveCD again and do a full re-install, using the option to overwrite and use the whole disk.

That will re-format the drive and all will be pristine again.

Regards,
Roger :cool:

---

### Post by ryanVickers on 2007-05-28
If you have nothing that can't be lost than you have everything can be lost :p

But yes, that should work fine!

---


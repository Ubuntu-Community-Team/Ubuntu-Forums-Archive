---
title: "What's a compatible pci 56k modem?"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by wbeck85 on 2005-07-30
I am looking for suggestions for an inexpensive, good performing, linux compatible 56k modem that will work plug-n-play with ubuntu.

I am trying to setup a small server for my home that will be a print server, a file server and an internet gateway. I only have access to diaup as the cable people refuse to run a line up my road and the nearest dsl station is over 4 miles away. So i'm stuck with dialup. Currently I have this thing running off of win2kpro, but I want to dump that and run it on ubuntu. Unfortunately, none of the pci modems I have tried are recognized by ubuntu. The problem is that they are winmodems, i think. I have scavenged them off of old computers that I have found. The newest one being about 3 years old. THe oldest one is from 1999.

What have you guys found to work?

---

### Post by heimo on 2005-07-30
Anything external. Serial modems will work very well. No autodetection, I think - so autodetection will not fsck up. ;) Learn how to setup one (quite easy), and you'll have very reliable connection method. (Check that your computer has serial connector, not all new ones have.)

---

### Post by wbeck85 on 2005-07-30
[QUOTE=heimo]Anything external. Serial modems will work very well. No autodetection, I think - so autodetection will not fsck up. ;) Learn how to setup one (quite easy), and you'll have very reliable connection method. (Check that your computer has serial connector, not all new ones have.)[/QUOTE]
 THanks for the advice.

I just bought a serial modem. Diamond SupraExpress 56K V.92 External. I read a review and it sounded kinda nice. Relatively cheap to 9 bucks on ebay (though the seller charged 10 for shipping, so 19 bucks total). I dont think that is too bad. Well, I'm looking forward to setting up this server. It should integrate the 5 computers in my house :)

---

### Post by wbeck85 on 2005-08-09
[QUOTE=wbeck85]THanks for the advice.

I just bought a serial modem. Diamond SupraExpress 56K V.92 External. I read a review and it sounded kinda nice. Relatively cheap to 9 bucks on ebay (though the seller charged 10 for shipping, so 19 bucks total). I dont think that is too bad. Well, I'm looking forward to setting up this server. It should integrate the 5 computers in my house :)[/QUOTE]
 Alrighty, heres a quick update:

This diamond serial modem works very well. The connection speed does not seem to be much better (31.6kbps says win2kpro) than when i was using a winmodem in Win2kpro on my 500mhz box, however, i think my pings are lower (about 130ms vs 180ms or so to ping google.com) But the beauty is that I can ACTUALLY connect to the internet in ubuntu now!
I use pppconfig and pon and poff and it works very well.

---

### Post by heimo on 2005-08-09
Great to hear it works! (and $19 with shipping is not bad!) I've found external modems to be trouble-free once configured. There are probably some tweaks you can make to Firefox to speed page loading and when I had a mobile dialup via gprs, I found that setting up local DNS cache made things a bit smoother.

As you said, most important that it works reliably. :)

---


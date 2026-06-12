---
title: "4gig dualchannel ram vs 6gigs ram? performance hit?"
date: 2010-01-03
forum: Hardware
---

### Post by binskipy2u on 2010-01-03
I'm using 64bit kubuntu...with NO swapfile (swappiness=0) and it runs FAST.. cant complain, er.. NO complaints.. i came into 2 gigs of the same speed pc5300 ram.. will I take a performance hit due to the way 4 gigs of dual channel work, compared to that 4gigs+2 gigs of "non" dual channel ram?  just wondering..
the 2 gigs is kinda sitting around doing nothing so to speak..
thanks

---

### Post by tgalati4 on 2010-01-03
On my 3 GHz Pentium D machine running Intrepid 64-bit, I got a 9% improvement in speed (using memtest) using dual-channel mode for 2 GB vs 3 GB.  So you need to evaluate your need for extra RAM versus "hands-on" speed.

I also got an extra 10% speed by pushing 4-4-4-12 speed versus the normal CAS speed ratings (5-5-5-15 I believe).  Run your memtest for 20-30 complete cycles at the turbo settings to make sure your RAM and motherboard are stable at the higher speed settings.

---

### Post by binskipy2u on 2010-01-03
it doesnt say the ram i have is dualchannel, but it came in the same computer i acquired and it came with it.. is it possible it "would"work dual channel?
besides doing mem tests and messing with the bios, is there' an easier,faster way to be able to know if the 2 gigs makes the total 6 gigs non dual channel or 6 gigs dual channel?

the dual channel is 2 X 2gigs in 2 slots, 2 more slots (4 total)
the other ram is 2 @ 1gig each

---

### Post by cascade9 on 2010-01-04
Normally, if you have 4 slots, and your motherboard is dual channel capable, installing 2 extra sticks will keep dual channel running. Proviso- you need to have the sticks in the right slots (check with your manufacturer to know for sure) and you need to have the same sized sticks for each 'pair' of slots. (normally slot 1 + 3 are paired and slot 2+ 4 are paired).  

So if you have 1GB in slot 1 and 1GB in slot 3, that is dual channel. Putting 2GB in slot 2 and 2GB in slot 4 would keep dual channel going.

---

### Post by binskipy2u on 2010-01-04
so whatever 2 channels are open (slots) put the 1 gig in each one of them, and that should for all intensive purposes run all 6 gigs total in dual channel (unless there's major differences in the brands of ram of the 2@ 1gig sticks in the other computer i have.. ?

---

### Post by cascade9 on 2010-01-05
Yep. 

Well, it should do anyway. Even with different brands of RAM. 

I'd be careful though, if your running dual channel then your speeds will be that of slowest stick.

Eg- 2x2GB DDR2 800, 1x1GB DDR2 667 1x1GB DDR2 533. In this case your dual channel speed will be 533..and that would be quite a bit slower than 800Mhz.

---

### Post by binskipy2u on 2010-01-05
its all pc5300

the 2 in the computer now are the same brand,speed
and the 2 in the other comptuer are the same brand and speed..
so it should be fine..

thanks for your help

---


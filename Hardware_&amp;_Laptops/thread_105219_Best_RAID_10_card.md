---
title: "Best RAID 10 card"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by Connollyir on 2005-12-17
I am looking for the best RAID 10 card that is compatible with Debian/Ubuntu. I want a card that is reasonably inexpensive (around $110) and can utilize SATA-150. I found a few but I couldn't find out wether they would roll with Breezy or not.

Does anyone have experience with this in Ubuntu? 

My end-goal is to create a fast, stable and secure array that would give me about 1 tb of space (it was RAID 5 or 10 and I think I'm going with 10 for its performance and fault tolerance - I need a way to back up my data in the event of a drive failure).

Advice is appreciated

---

### Post by Connollyir on 2005-12-19
*bump* Are there any known cards that work with Ubuntu?

---

### Post by spade_shark on 2005-12-21
So you want to open a can of worms ey?  First, for the price you want ($100.00) and change, it will be software raid.  Second, for the space you want (1+ TB) you will need four (4) 500GB Sata drives.  FYI ( Seagate - Barracuda 500GB-16MB - 7200RPM -- ST3500641AS ) $350.00 ea.  :???: Ouch.  Maybe spend some more on the card and go with a hardware eight port and use 8 cheaper 250gb drives.  Raid 10 can be also 'spanned' across controllers, which can result in some cool combos. :cool:    Lots to think about, unless you have a lot of moola (if you do great my address is...).

You are correct 

> I'm going with 10 for its performance and fault tolerance 
  Yes I agree, if you are using it for a database (exchange with 4000 current users).  Maybe try to rethink Raid 5 for that much space.  Raid 5 and Raid 10 are very close for the benchmarked results, when they are both healthy.  Raid 5 takes a hit when one drive is offline, so swap the bad one out wait and hour and continue :)   

Pls., no flame war over the Raid 5 vs 10 details folks.

Crack open a can o'caffine and continue here.  

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)  Goodluck :)  

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks]("http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks")

P.S. after you tweak the snot out of it, it works great!  Post back and let us know what your thoughts are...we can get it to work.

---

### Post by Connollyir on 2005-12-23
[QUOTE=spade_shark]So you want to open a can of worms ey?  First, for the price you want ($100.00) and change, it will be software raid.  Second, for the space you want (1+ TB) you will need four (4) 500GB Sata drives.  FYI ( Seagate - Barracuda 500GB-16MB - 7200RPM -- ST3500641AS ) $350.00 ea.  :???: Ouch.  Maybe spend some more on the card and go with a hardware eight port and use 8 cheaper 250gb drives.  Raid 10 can be also 'spanned' across controllers, which can result in some cool combos. :cool:    Lots to think about, unless you have a lot of moola (if you do great my address is...).

You are correct 

 
  Yes I agree, if you are using it for a database (exchange with 4000 current users).  Maybe try to rethink Raid 5 for that much space.  Raid 5 and Raid 10 are very close for the benchmarked results, when they are both healthy.  Raid 5 takes a hit when one drive is offline, so swap the bad one out wait and hour and continue :)

Right now, Breezy requires some 'tweaks' or a crunch for most RAID cards to get to roll.     

Pls., no flame war over the Raid 5 vs 10 details folks.

Crack open a can o'caffine and continue here.  

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)  Goodluck :)  

P.S. after you tweak the snot out of it, it works great!  Post back and let us know what your thoughts are...we can get it to work.[/QUOTE]

I was originally concerned about the performance issues with RAID 5 after a disk failure and I also read that there is a write-to-disk performance drop from 10 to 5 ([http://www.pcguide.com/ref/hdd/perf/raid/levels/multLevel01-c.html](http://www.pcguide.com/ref/hdd/perf/raid/levels/multLevel01-c.html)) which is why I opted for RAID 10. The more I think about it the more I realize that the 10 array is not designed for my application, that being a large storage database for few users (x >10), and I should probably go with 5 to save cost and sanity. 

I do, however, want good performance from the server over gigabit ethernet and 10 base T, i.e. streaming media, downloads and uploads should all run as fast as possible given hardware limitations. I'm not expecting magic here but I don't want my RAID array to be the limiting factor - if it even comes down to that and I'm not sure that the network could be fast enough to outpace the drives, its just a concern that came to mind. There isn't going to be a bunch of traffic coming into the server, what a typical load could be would be 2-5 clients streaming non-copywrited audio and video files while concurrently 2-5 other users would download other files - be it audio or video - and that would be heavy traffic for its application.

I'm doing my homework a long time in advance.

Thanks

-Ian

---


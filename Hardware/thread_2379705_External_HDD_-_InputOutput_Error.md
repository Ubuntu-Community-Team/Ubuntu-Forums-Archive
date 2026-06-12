---
title: "External HDD - Input/Output Error"
date: 2017-12-08
forum: Hardware
---

### Post by kitfreidge on 2017-12-08
I was watching on my hard drive when I accidentally let it fell down on a short distance while it was reading.
I immediately tested it, but then I got no luck. I only get Input/Output error at first, but there are times that the hard drive would actually read
and I could place some files inside and transfer it to another computer. However, still the hard drive is still not fixed permanently, or at least prolong its life.

For some additional information:

The hard drive is a **WD Passport Ultra 2TB**
I tried fixing it with fsck but got no luck.
Even tried using smartctl, but sadly it says it doesn't support it.
I managed to backup my files using testdisks, so completely washing out the hard drive is totally fine.
The hard drive doesn't make any weird noises, except a sound of interruption kick (Idk how to explain) and it cycles every like 5 mins. give or take.
Lastly, I tried using different ports and connectors.

I hope anyone could help me since, it's just a 5 month hard drive, and the retailer said I can't get it fixed under warranty. (it's a long story) (though, short story: I lost the warranty papers).

Thanks.

---

### Post by Autodave on 2017-12-08
I would believe that the HD has suffered irreversible damage in the fall.

You can get everything off of it that you can and then remove all partitions. Then crate a new partition(s) and try formatting them.

For instance: if you were to create 2 partitons of 1TB each, you may get reported that one partition is good but the other bad. At least you would have 1TB to use.  You could also try 4 partitons and possibly have 3 to use. Etc.

---

### Post by sccman on 2017-12-08
I agree with Audodave. The hard drive probably suffered from irreversible damage.

Other than what he suggested, I would make sure the connections to the hard drive and computer are secure. Sometimes if the plugs aren't in all the way it could create issues.

---

### Post by kitfreidge on 2017-12-09
I see. I guess I should try partitioning the hard drive then. My last resort before I give up on it. Anyways, thanks for all your efforts. :)

---


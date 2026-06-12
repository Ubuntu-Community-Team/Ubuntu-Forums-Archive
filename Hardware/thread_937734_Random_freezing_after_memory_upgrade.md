---
title: "Random freezing after memory upgrade"
date: 2008-10-04
forum: Hardware
---

### Post by hfilter on 2008-10-04
Hi

I have recently upgraded my Dell XPS M1330 from 2Gb ram to 4Gb. (I bought
 2 x 2GB Corsair DDR2 667mhz 200-pin)

Since then my system freezes at a random time (anything between 5min and 4h) after booting. It freezes so bad that it leaves me no option but to power it down manually. I use Hardy 64-bit.

I have run the memory test from the Ubuntu boot menu for 18 passes without finding any errors.

I cannot find anything in the logs that looks suspicious at the time of the freeze either.

I updated my bios to the latest version (A11).

When I boot into windows it also works fine for a while but then suddenly gives a BSOD before restarting automatically.

If anyone could help me to troubleshoot this problem I would really appreciate it!

Thank you,
Heinrich

---

### Post by lisati on 2008-10-04
It is possible that your memory isn't being properly recognized or some such problem.

A month or two back I was getting the BSOD regularly with XP on my desktop, and one time I noticed that Ubuntu seemed to freeze on shutdown. One thing I noticed when Ubuntu froze, the scroll-lock light and Caps-lock light were lit up, which is sometimes the case when *ubuntu has no other way of letting you know there's a problem. 

*Paying attention to the messages XP provided led me to check the extra memory I'd installed some time earlier:* powering down the computer, removing and reinstalling the extra memory card seems to have cured the problem.

---

### Post by hfilter on 2008-10-04
Thanks, lisati

I'll look out for the scroll- and caps-lock lights.

I'm currently running with just one of the 2GB modules (which I removed and then reinstalled). I hope this may narrow down the problem a bit.

Does anyone else have any suggestions?

Thanks again!

---


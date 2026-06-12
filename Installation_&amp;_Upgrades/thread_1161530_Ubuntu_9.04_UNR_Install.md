---
title: "Ubuntu 9.04 UNR Install"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by simoncifer on 2009-05-16
Hi, just want to let people know that I have successfully installed Ubuntu 9.04 UNR on a desktop computer: AMD Athlon(tm) 64 Processor 3500+, with 1GB DDR RAM, and a 4GB compact flash as hard drive (connected using IDE->CF).

I choose UNR mainly because of the 4GB CF card, hoping that UNR would have features that would be more gentle on the I/O to the CF card than regular installation.

But I saw was that UNR automatically created a swap partition on the CF card (I let the installer to create the partition automatically).  I read that swap partition on CF card would kill the card pretty quickly, so I swapoff and deleted that partition right away.

But what about swap file?  Is it also hurtful to the CF card?

Thanks in advance.

- Simon

---

### Post by Rocket2DMn on 2009-05-16
Linux doesn't use a swap file by default (though with some weird configurations, I believe it is possible to set it up).  With your swap partition gone, you won't be using any swap with linux, so it won't be a problem.  If you have enough RAM, you'll be fine using the system, you just won't be able to hibernate without any swap.

So to answer your question - no, it is not hurtful because there is no swap file.

---

### Post by simoncifer on 2009-05-17
That's good to know that a swap partition or a swap file is not required for Linux.

Thanks.

- Simon

---


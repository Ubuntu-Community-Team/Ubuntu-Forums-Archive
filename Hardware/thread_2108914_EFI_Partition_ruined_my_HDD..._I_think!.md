---
title: "EFI Partition ruined my HDD... I think!"
date: 2013-01-26
forum: Hardware
---

### Post by pattmayne on 2013-01-26
I can't access my HDD (Drive D).

After having trouble installing Ubuntu on my new EFI system, I couldn't boot either of the OS on my SSD (Drive C). I fixed that problem by running boot-repair, allowing me to boot Windows 8 again. But that created a new problem... I can no longer access my D drive (HDD)... in Windows it says "D is not accessible: The parameter is incorrect."

I tried to format it, but the capacity just says 97 GB when it's really a 2TB HDD.

So I looked it up two ways: in the partition manager on my live USB, and in a program called "GetDataBack for NFTS." They both say that my HDD is an EFI system partition. Is this why I can't access it? Was this done by my boot-repair???

SCREEN CAPTURE: Here is the URL to a screen-capture:

[http://www.spacewineries.com/problem33.gif](http://www.spacewineries.com/problem33.gif)

I'm concerned mainly with the highlighted partition... the 1st HD with two partitions. (Although I think I screwed up the boot-loader on the 2nd HD which now has 9 partitions.

SO: Can someone tell me if I'm right? I feel like this highlighted partition should NOT be an EFI system partition and that I should somehow convert it back to... whatever it was (LoL). I guess I'll do ext3 or NFTS but I don't remember its original file system. Is this dangerous? Will I screw everything up? What should I do??

Thanks.

---


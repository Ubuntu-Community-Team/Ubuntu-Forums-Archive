---
title: "Amazing SD card behavior / a simple reboot changes the SD card capacity !"
date: 2023-01-25
forum: Hardware
---

### Post by jacques-t on 2023-01-25
In the last few days, I was testing a procedure involving copying a 32 GB .img file to a 32 GB SD card.

It was working very well until yesterday, when my "dd" copy started to fail after 16 GB, saying that the destination device was full.

fdisk was reporting an actual SD card size of 16 GB, while the real capacity is 32 GB, explaining why dd complained.

This has happened with Sandisk and Samsung 32 GB cards, all sourced from mainstream suppliers.

At some point, I was so puzzled that I decided to reboot my Ubuntu 20.04 workstation.

And after reboot, all SD cards were back to their real 32 GB size...!

Although my issue is resolved, I really would like to understand how this situation can arise, and why a simple reboot can change how the operating system interprets the hardware SD card geometry.

Thanks for any insights you might have !

JL, Montreal

---

### Post by TheFu on 2023-01-25
Flash storage wears out.  You are probably seeing early signs of that.  Count yourself lucky that it didn't just stop working one day.

I think most cheap SDHC flash storage has about 1000 writes per sector. Better models have 100,000 writes per sector.  Some models from Sandisk have a lifetime warranty ... in countries where that isn't allowed, it is 30 yrs, so that's pretty impressive.  I was looking at a Sandisk Extreme PRO model with that warranty.
If you are copying over data daily 3 times and do that for a year, you are over the normal write limitation for cheap cards.  Of course, there are different models with more and less write count designs and every flash cell has a different actual number of writes it will support.

If you are worried about bad storage, perhaps use ddrescue, not dd.  ddrescue has some error correction that dd doesn't.

BTW, after format, a 32G flash drive is probably only 29G usable storage.  That might or might not be important.  The file system used would matter too.  For Linux on flash (USB or SDHC), I'd use f2fs for the file system.  For Windows, I'd use exFAT.  Both are specifically designed for SDHC storage and have fewer writes than other file systems.  f2fs supports native Linux permissions, users, groups, etc. The way it reduces the writes is by not being journaled. That's good for reducing writes, bad for data corruption issues.

---

### Post by jacques-t on 2023-01-27
Thank you for your reply, but I do not think it has to do with the SD cards (I tested many, few of them being brand new), but more with Ubuntu itself. The fact the the SD card sizes jumped from 16GB to 32Gb after a simple reboot is scary. JL

---

### Post by TheFu on 2023-01-27
> **jacques-t said:**
> Thank you for your reply, but I do not think it has to do with the SD cards (I tested many, few of them being brand new), but more with Ubuntu itself. The fact the the SD card sizes jumped from 16GB to 32Gb after a simple reboot is scary. JL

There are lots of fake flash storage devices in the world.  "Mainstream" suppliers isn't clear.  Amazon has issues with fake flash storage.  When I really need it to work, I go to 2 specific, big-box, retail stores to buy flash storage. If I have some time, I'll try to order from Amazon, but directly from the vender with the name on the card - "SanDisk Store" or "Samsung Store", for example.  I've had good luck with Samsung PRO Extreme microSD storage. So far, none has failed ever, but they are only 3 yrs old.  Quality from both, if we get the real product, not a fake, has been excellent.

Wish I had a better answer.  I've just never seen the behavior described.

Maybe someone else has ideas that don't include fake storage?

---


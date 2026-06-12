---
title: "How fast really it's a SD card?"
date: 2008-10-30
forum: Hardware
---

### Post by proteo on 2008-10-30
Hi!

I installed Intrepid Ibex RC last week on my laptop, and almost everything is working just fine. After installing and configuring all the stuff I use, I started migrating the files from my Desktop and found that the 8GB SDHC Card that I'm using it's only being read at 2MB/s on the card reader from the laptop, since it's a class 6 card (at least 6MB/s writing and faster for reads), I think it should be a lot faster. It's there any way to speed up the card reader? or it's as fast as I can get? How fast are yours?

Thanks

---

### Post by prshah on 2008-10-30
> **proteo said:**
> at least 6MB/s writing and faster for reads
How fast are yours?


Using a 2Gb SD card (not mini, micro) and get consistent write speeds of nearly 6MB/s, on Ibex and Gutsy. Maybe you need to run an fsck on the card?

---

### Post by proteo on 2008-10-30
I tried erasing everything on the card, and copying some large files back, the card wrote at 13~12 MB/s, but reading the files back to the laptop it's still 2.3MB/s, this is getting weirder...

I'll try to run fsck and maybe reformat the card.

---


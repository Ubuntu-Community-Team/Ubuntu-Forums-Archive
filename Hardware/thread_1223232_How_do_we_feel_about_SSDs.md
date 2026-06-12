---
title: "How do we feel about SSDs?"
date: 2009-07-25
forum: Hardware
---

### Post by josephellengar on 2009-07-25
I'm considering a laptop that has an option for a 160gb ssd + 500gb 5400 rpm hard drive.  I guess if I got it I'd just use the 5400 rpm for data storage and put both of my operating systems on the SSD.  So, is it worth it?  It's significantly more expensive than just one 500gb 7200 rpm drive.  I guess that the wear leveling would keep the drive alive more than long enough, correct, at least 4 years or so?  I've heard that ext3/4 journaling can wear down a SSD pretty quickly.  Is that correct?  I don't want to have to replace it soon, but I would guess that modern drives would be able to deal with that, especially since this is an Intel drive.  So, what do you think?

---

### Post by philcamlin on 2009-07-25
i have ubuntu on a netbook with a ssd its good i dont see any issues so far im using ext3 

:popcorn:

---

### Post by bear24rw on 2009-07-25
love em

---

### Post by philcamlin on 2009-07-25
you cant loose your data either :popcorn:

---

### Post by zipakna on 2009-07-26
hi newbie here, my very first install of ubuntu was on a Transcend 64 gig IDE ssd. my second install is on a brand new wd 250 gig standard hdd 5400 rpm the ssd is a lot faster. third install is on a transcend 64gig sata 300  ssd. you dont see the ubuntu loading screen, it just goest right from bios to login.

---

### Post by josephellengar on 2009-07-26
> **zipakna said:**
> hi newbie here, my very first install of ubuntu was on a Transcend 64 gig IDE ssd. my second install is on a brand new wd 250 gig standard hdd 5400 rpm the ssd is a lot faster. third install is on a transcend 64gig sata 300  ssd. you dont see the ubuntu loading screen, it just goest right from bios to login.

Wow.  Thats FAST!  But, would I expect them to wear out, or is the wear and tear no worse than on a regular hard drive?  Did you notice any difference in battery life?

---

### Post by IcarusR on 2009-07-26
Battery life will be better with SSD, due to lack of moving parts. 
Heat will also be decreased for the same reason.

---

### Post by josephellengar on 2009-07-26
> **IcarusR said:**
> Battery life will be better with SSD, due to lack of moving parts. 
Heat will also be decreased for the same reason.

I know that it should be better in theory.  I'm wondering about in practice.  I've heard some people say that the difference amounts to four or five minutes when going from a platter to a ssd.

---

### Post by vegetarianshrimp on 2009-07-26
SSD's are GENUIS!! [size=1](tiny too)[/SIZE]

---

### Post by josephellengar on 2009-07-26
> **vegetarianshrimp said:**
> SSD's are GENUIS!! [size=1](tiny too)[/SIZE]

Could you share your experience?  I just want to know if I have to worry about it wearing out quickly still.  I heard that in the beginning they wore out really quickly and that journaling filesystems such as ntfs or ext3/4 could kill them.  Do I still have to worry about that?

---

### Post by Friqenstein on 2009-07-26
'We' love 'em.

Seriously though, I've had my current laptop for over a year now (almost 2 years) and it came with an 80GB SSD. I was worried at first about the same reasons as most people, but Ubuntu quickly set my mind to ease. I've been using HardyHeron 8.04 for about a year now and I've never had any issues with my SSD.

It's quieter, less of a heat generator, and not susceptible to excessive vibrations. I work in an environment where my laptop is subject to constant low frequency vibrations for 24 hours a day, and this will kill any normal HD in no time flat.

As for the read/write capabilities... I've hear a lot of people talking about 'you only get X amount of usage from SSD just like flash' I'm not so sure about that. I'm constantly writing and re-writing data to my SSD every day. I have not hand any problems at all.
I would recommend SSD over a normal drive any day of the week.

Hope that helps.

---

### Post by vegetarianshrimp on 2009-07-26
Mine (on my netbook) has been working fine. I've only had it for 6 months though, I don't know what will happen to it in 4 years.

---

### Post by bad_crow on 2009-07-26
SSD will work fine on most of the filesystems, however some filesystems are getting optimised for this kind of drive (BTRFS at least, but it's still highly experimental so I won't recommend it).
I think EXT4 should perform very well with an SSD drive because it's one of the fastest (the fastest ? ) filesystem nowadays.

For the SSD, you have to be very careful when buying it. There is indeed several generations, with completely different performances. 
they are globally stable, even if intel had some problems (now solved by firmware), the SSD was getting slower with the time.

A SSD should work for several years in daily usage, I think 3 to 5 years depending on the model, so you'll probably change it before he dies (like we do now for classical hard drives).

I don't have one to share my feelings about it (I haven't got the money to buy and test one yet, even if I want to), but I said what I think about them reading over the internet.

---

### Post by Anthon on 2009-07-26
I have my home directory on an encrypted filesystem (which is automatically mounted on login) on a 16Gb SD Card. 
I actually do a regular backup as sometimes the SD card seems to go nuts, or the controller on the card. After slightly more than a year of usage I had to buy a new card because of controller problems. Both the old and new card were  SanDisk Ultra 2 SDHC (Full size SD). The card itself is formatted with ext2, the file with the encrypted filesystem on the card is ReiserFS. 
ReiserFS' journalling saved a bunch of work several times.

As my homedirectory is easily moved between my desktop machine and my two laptops. And in my EEEPC 901 it is just in the provided SD slot and the machine is easy to take along.

BTW I had some problems with HDSC cardreaders. My Sandisk multicard reader is fine, but a Sharkoon multicard reader that I build into my PC has severe problems with the load of writing/reading the card.

---

### Post by josephellengar on 2009-07-26
Thank you very much for your input everybody

> **Friqenstein said:**
> 'We' love 'em.

Seriously though, I've had my current laptop for over a year now (almost 2 years) and it came with an 80GB SSD. I was worried at first about the same reasons as most people, but Ubuntu quickly set my mind to ease. I've been using HardyHeron 8.04 for about a year now and I've never had any issues with my SSD.

It's quieter, less of a heat generator, and not susceptible to excessive vibrations. I work in an environment where my laptop is subject to constant low frequency vibrations for 24 hours a day, and this will kill any normal HD in no time flat.

As for the read/write capabilities... I've hear a lot of people talking about 'you only get X amount of usage from SSD just like flash' I'm not so sure about that. I'm constantly writing and re-writing data to my SSD every day. I have not hand any problems at all.
I would recommend SSD over a normal drive any day of the week.

Hope that helps.

---


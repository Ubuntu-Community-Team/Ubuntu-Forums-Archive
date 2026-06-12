---
title: "Solid State in Laptop"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by Apreche on 2007-10-13
So, I've got a Fujitsu P7230. It came with a 40 gigabyte 1.8" Toshiba hard drive. The drive isn't completely dead yet, I can still mount it and such, but all indications point towards it being very close to death. It doesn't matter so much because I don't store important data on the laptop hard drive anyway. 

So, I'm considering buying [this Samsung solid state drive]("http://www.newegg.com/Product/Product.asp?item=N82E16820147020"). I checked, and it has the same connector as my current drive, and is the same size. I also checked, and I only need about 4G of space for my purposes, so the 16G model is more than enough for me. Though, I do have some concerns.

First of all, I know that solid state drives can only survive for a limited number of writes. Is there some way to limit the number of writes to the drive to prolong its life? Perhaps I can move logging to a RAM drive of some sort? Are there any other frequent writes that Ubuntu does that I need to eliminate?

Secondly, I know that the Toshiba drive currently in the laptop is ATA6, but the Samsung is ATA5. Obviously if it does work, it will be slower than some other drive I might get, but will it work at all? I've also heard of other people who try to use solid state drives under Linux having performance issues as well. Such as in [this thread]("http://ubuntuforums.org/showthread.php?t=573219"). Will I have these issues?

Thanks for any help and information you can offer. I'm beginning to think this is the one time I will make a risky technology purchase. Somebody's got to try it, this time it might as well be me.

---

### Post by thelocust on 2007-10-14
They degrade after a certain number of writes but they will still last longer than any regular HDD so it's nothing to worry about.

---

### Post by hessiess on 2007-10-14
from what i understand if thay fail there is no way to recover the data, hard drives can almost alwase be recoverd, atleast partitioly

---

### Post by tgalati4 on 2007-10-14
They tend to be slower than normal disks for writing because they have to go through an extensive striping algorithm to prevent over use of a given area.  The Emphase 4 GB drives that I am testing have a 4-million write cycle capability, but I had a few duds in a batch of 10.  I'm using them with Damn Small Linux, running completely in RAM.  The drives are only used for loading the initial OS into RAM and dumping logs back to disk during shutdown.

Let us know how it works.

---

### Post by Apreche on 2007-10-16
Well, I got the drive. I swapped it out for the dead drive and installed Gutsy RC1.It just works. My computer is silent, the batteries are lasting an hour longer according to powertop, and the machine boots a bit faster. All in all, I say it's a success. 

I do know that it can only handle a limited number of writes before its game over. I disabled the logging services to try to minimize writing. Any other suggestions as to how to minimize writes and extend the life of the drive?

---

### Post by MidBSD on 2007-10-17
The number of writes depends on what technology is used. CF commonly lasts 10,000 writes and will probably only survive a year.

Other technologies will last 100,000 writes and combined with 'wear levelling' technology, will outlast a traditional HD.

I was going to buy 2 x 32GB CF cards and mount them on a dual CF to IDE converter and replace my laptop HD but without wear levelling and only 10,000 writes I figured it wouldn't last long.

---

### Post by Apreche on 2007-10-17
> **MidBSD said:**
> The number of writes depends on what technology is used. CF commonly lasts 10,000 writes and will probably only survive a year.

Other technologies will last 100,000 writes and combined with 'wear levelling' technology, will outlast a traditional HD.

I was going to buy 2 x 32GB CF cards and mount them on a dual CF to IDE converter and replace my laptop HD but without wear levelling and only 10,000 writes I figured it wouldn't last long.

I think I'm ok then. My drive is definitely not CF. Samsung even claims 2,000,000 operating hours, which is a joke, but hey.

---


---
title: "Good IDE Controller/RAID card?"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by thrift on 2005-05-27
Hey everybody.  

I have 3 ide harddisks that I would like to set up in an EVMS RAID 5 in Ubuntu(Warty/Hoary/Breezy), but I have had a lot of problems finding cards with support.  

I started out with a highpoint rocket raid 404 and ended up having hardware problems and finding they have 1 U.S. representative who does both technical support and customer server, so they sent me a updated version of the rocketraid 404 and I experienced nothing but problems.  After this I found a website advertising some lower end Pacific Digital cards as having linux support, but soon after I purchased them I found that they were misadvertised and that only higher end models have linux support, now they have been returned and I'm ready to take another go at this.

I am trying to stay in around a $100 budget(If a proven solution is available for not much more I am interested).  I would like to gain 4 IDE channels and it really doesn't matter to me if they are on one card or not.  It would be nice if it was a major brand.  It would also be nice if the drivers for this card are in the vanilla Linux kernel.  It wouldn't hurt to have the manufacturer actually support the driver.  It would be good if the card had the option to do hardware RAID in Linux, but as I plan to do software RAID, really whatever will give me the best performance with the least hastle and will not cost me an arm and a leg for EVMS RAID is what I am after.

Even if anyone knows a place where I can get a list of well supported Linux IDE cards/chipsets that would be helpfull, but if anyone has already solved this exact problem I'd rather use an experienced solution.

Thanks in advanced to everyone who can provide some help.

---

### Post by MrTom on 2005-05-28
[QUOTE=thrift]Hey everybody.  

I have 3 ide harddisks that I would like to set up in an EVMS RAID 5 in Ubuntu(Warty/Hoary/Breezy), but I have had a lot of problems finding cards with support.  

I started out with a highpoint rocket raid 404 and ended up having hardware problems and finding they have 1 U.S. representative who does both technical support and customer server, so they sent me a updated version of the rocketraid 404 and I experienced nothing but problems.  After this I found a website advertising some lower end Pacific Digital cards as having linux support, but soon after I purchased them I found that they were misadvertised and that only higher end models have linux support, now they have been returned and I'm ready to take another go at this.

I am trying to stay in around a $100 budget(If a proven solution is available for not much more I am interested).  I would like to gain 4 IDE channels and it really doesn't matter to me if they are on one card or not.  It would be nice if it was a major brand.  It would also be nice if the drivers for this card are in the vanilla Linux kernel.  It wouldn't hurt to have the manufacturer actually support the driver.  It would be good if the card had the option to do hardware RAID in Linux, but as I plan to do software RAID, really whatever will give me the best performance with the least hastle and will not cost me an arm and a leg for EVMS RAID is what I am after.

Even if anyone knows a place where I can get a list of well supported Linux IDE cards/chipsets that would be helpfull, but if anyone has already solved this exact problem I'd rather use an experienced solution.

Thanks in advanced to everyone who can provide some help.[/QUOTE]
 
I have had success with one of the cheapest IDE controller Cards on the market (SIL690 based), the drivers in linux are very robust. 

Yet i doubt you will find a hardware manufacturer willing to support a linux driver / kernel, if they do support linux it will be one or two distributions ie Redhat Linux Enterprise and/or SuSe Linux.

---

### Post by thrift on 2005-05-28
I can find no information about the SIL690.  Is this a typo.  What exact model of card do you have?  What kernel module does this card use?

I am kind of looking for something to the equivalance of nvidia graphics cards in linux(good open 2D drivers, supported proprietary nvidia drivers) or sound blaster live(good open support, I understand creative took a part in creating the drivers/tools), but with an ide card.  If it does turn out that there is no such hardware/company, then I'll have to try out something like what you've suggested, but I'll need to actually be able to find such a piece of hardware.

---

### Post by MrTom on 2005-05-28
Sorry the card was SIL680 based my bad. Seems to work ok. I don't really do anything intense with it.

---

### Post by thrift on 2005-05-29
Ok.  Thanks a lot.  I've done some more research on that card and it looks perfect.  Cheap, decent drivers, compatable RAID support in the Linux kernel if for some reason I needed it, and I found some companys releasing with that chipset who say it will work with Linux.

Looks perfect.  Going to order two tonight.
Thanks.

---

### Post by mozkill on 2007-11-14
Can someone recommend a good "hardware RAID" card for SATA in Ubuntu 7.10 ???   Recommending more than one would be useful as I shop around.  Thank you.

---


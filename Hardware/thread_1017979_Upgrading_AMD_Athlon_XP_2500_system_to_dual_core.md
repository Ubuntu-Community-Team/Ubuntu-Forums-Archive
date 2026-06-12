---
title: "Upgrading AMD Athlon XP 2500 system to dual core"
date: 2008-12-21
forum: Hardware
---

### Post by jtac84 on 2008-12-21
Hello, 
I have a system with an AMD Athlon XP 2500 CPU, cheap PCChips Mobo, 1g RAM, Radeon 9800 Pro Video card, Antec Sonata case w/ 380 W PSU, and a DVD RW drive.  The entire system is about 5 years old and I would like to upgrade to a dual core AMD X2 set up for as a low cost and be able to do everything in linux except gaming.

My first question is: Could I re-use my case/PSU being that its 5 years old, for a dual core system ?  I would like to create a system that is low power and enables me to use the existing Power Supply if possible. Would anybody recommend just dropping the cash for a new one after the 5 year mark on my 380 Watt?

Second, are there good mobos out there with onboard video that allow compiz and all 3d desktop effects to work perfectly in linux?  Without doing gaming on this machine, I'd like to be able to save the cost of a separate video card.

Third, what are your thoughts of the specs I have in mind:
-AMD X2 5000, or AMD X2 4850e (for lower power consumption)
-2G or 4G of DDR2 800 RAM
-200 to 500 GB HDD (standard)
-Onboard video if the system can handle everything except gaming
-Onboard sound card
-Lightscribe DVD RW


If anybody knows how to make a setup like this as compatible with linux as possible, please leave a comment. Is there anything that you think could make this better for linux or a faster/more efficient system?  It seems to me that it is pretty standard to be able to build a fully working system like this for under $400.  Thanks in advance for any comments.

---

### Post by Bucky Ball on 2008-12-24
That's looking good. As long as Ubuntu recognises the motherboard and cpu (the cpu should be fine, the motherboard is a question I can't answer, still researching myself) then hard drives and ram are the least of your worries and not normally a problem unless something particularly exotic.
That won't apply in this case.

I am about to build a computer for my mother-in-law and that is the same processor I chose tonight when figuring out the appropriate hardware for the job. You might be interested in these drives for power saving, you'll find they are same price if not a little cheaper than regular (and minutely cheaper over their lifetime due to savings on power bills!). I have one in a Coolermaster X-Craft fanless external case and it runs virtually cold and silent:

[http://www.wdc.com/en/products/products.asp?driveid=559&language=en](http://www.wdc.com/en/products/products.asp?driveid=559&language=en)

... and this in general:

[http://playgreen.org/Wiki/HowToBuildAGreenPC#S2](http://playgreen.org/Wiki/HowToBuildAGreenPC#S2)

Here are some ideas, although I am going to keep hunting for a motherboard:

[http://daveshields.wordpress.com/2007/09/10/building-your-own-linux-ubuntu-computer-using-the-ecs-geforce-6100sm-m-motherboard/](http://daveshields.wordpress.com/2007/09/10/building-your-own-linux-ubuntu-computer-using-the-ecs-geforce-6100sm-m-motherboard/)

At the moment, the system I am going to build is something like this, a variation of your plan and slightly more specific:

-AMD X2 4850e cpu 
-2G of DDR2 800 RAM
-180-320Gb x 1 and 500Gb Caviar Green HDD 
-Galaxy GeForce 8400GS PCI-E x16 512MB DDR2 64-bit (they'd like to edit video and possibly play resource-sapping games in the future)
-Onboard sound (card can be added later if required)
-Lightscribe DVD RW

One thing to remember is that the socket size should be the same for the processor and motherboard; in this case Socket AM2 or  AM2+ motherboard. If they aren't, all bets are off. But you probably knew that. :)

Good luck and let us know how you go. If I have any further insights I'll post 'em here.

ps: I would also be interested in all opinions regarding motherboards. User accounts are always the best - all the gear I have listed in my signature works great if anyone might finds that a help one of these days!

---

### Post by cariboo on 2008-12-24
I would suggest upgrading the power supply, as the output may be a little bit low for your needs, also it may not have all the connectors you need to power your equipment. If you already have Ubuntu installed on a hard drive, just plug it in and your ready to go. For a all-in-one motherboard, I would suggest getting one with and Nvidia graphics adapter, as they seem to be better supported than ATI.

Jim

---

### Post by MonkeyPaw on 2008-12-24
Your 380W PSU should be enough as long as it has the necessary connectors to the motherboard. Today's boards usually have both the 4pin CPU and the 24pin ATX (up from 20pin of yesteryear). Even then, you can buy a 20pin to 24pin harness to fix that issue. 380W is plenty for most systems, even those with a dedicated video card. With what you are talking about building, I'd say you're maybe going to use 225W total. Adding extra drives will make a difference, but so long as your old PSU is a quality brand and in good shape (not clogged with dust or operated under tough conditions), you'll be fine. Of course, all PSUs have a lifespan, and you don't want them to go "pop" while in use, as they often take components with them. I say that you can get by for now to save on your initial expenses, but I would consider replacing it in the next year or so.

As for what chipset, I say go with an nVidia-IGP model. The 6100/6150 should be good enough for non-gaming while still providing good desktop support, and it's pretty darn cheap.

---

### Post by mpsii on 2008-12-24
I would say, if your new motherboard supports AGP (unlikely not improbable) reuse your ATI 9800. Otherwise, you can find a PCI-E discrete ATI or nVidia card for around $30 on eBay. Discrete graphics will almost always be better than onboard graphics. Even if you are not gaming, some of the desktop effects or video decompression will be better on a discrete card.

Besides, with the 9800, you can still do some decent gaming.

---


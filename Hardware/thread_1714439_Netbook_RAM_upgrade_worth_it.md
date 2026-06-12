---
title: "Netbook RAM upgrade worth it?"
date: 2011-03-25
forum: Hardware
---

### Post by bumder on 2011-03-25
I'm currently running Lucid on a Samsung NC10 with 1Gb of RAM. 
Performance isn't too bad, but not great when using Banshee, or watching flash videos in FF/Chrome.

My question is if I add another 1Gb of RAM giving me 2Gb in total, am I likely to actually notice a difference (thinking it might be more CPU oompf related)

Cheers

---

### Post by .:PiXi²:. on 2011-03-25
Have a look at the CPU usage of Banshee and the Flash player. If you have 1GB RAM and a 1.6 GHz CPU, the CPU would probably be the bottleneck.

---

### Post by Yellow Pasque on 2011-03-25
Use htop and free -m to figure out what the bottleneck is:
```
sudo apt-get install htop
htop
free -m
```

---

### Post by bumder on 2011-03-26
System Monitor shows Banshee @ 10% CPU/30Mb memory, Chrome @ 90-100% CPU/40Mb (couple of tabs and flash vid), gnome-system-monitor @ 20% CPU/5Mb, pulseaudio @ 8% CPU/6Mb.

The biggest memory draw of all the processes is either web browser or banshee, and even then its like 50Mb.

Guess it is the CPU then :(

---

### Post by ronnielsen1 on 2011-03-26
I always encourage people to upgrade their ram as much as possible. One of the best upgrades and the longer you wait, the more expensive the memory gets

---

### Post by Anthraxinsoup on 2011-03-26
> **ronnielsen1 said:**
> I always encourage people to upgrade their ram as much as possible. One of the best upgrades and the longer you wait, the more expensive the memory gets
Not trying to be a jerk here, but RAM is only really needed past 4Gigs if you are doing insane stuff. One I find a job I will go past 4gigs, but most people, and by most I mean 99% only need 4gigs. 8Gigs is just nice to have.

---

### Post by ronnielsen1 on 2011-03-26
Um, original post:

> I'm currently running Lucid on a Samsung NC10 with 1Gb of RAM. 
Performance isn't too bad, but not great when using Banshee, or watching flash videos in FF/Chrome.

My question is if I add another 1Gb of RAM giving me 2Gb in total, am I likely to actually notice a difference (thinking it might be more CPU oompf related)

Cheers

Your post:

> Not trying to be a jerk here, but RAM is only really needed past 4Gigs if you are doing insane stuff. One I find a job I will go past 4gigs, but most people, and by most I mean 99% only need 4gigs. 8Gigs is just nice to have.


Not sure how you're doing your math but anyway, 5 yars ago we wouldn't have imagined using the amount of ram that is used nowadays. It's cheapest when it's new and it makes LOTS of difference.
I believe 2G over 1G on his box would make a lot of difference

---

### Post by Anthraxinsoup on 2011-03-26
> **ronnielsen1 said:**
> Um, original post:



Your post:




Not sure how you're doing your math but anyway, 5 yars ago we wouldn't have imagined using the amount of ram that is used nowadays. It's cheapest when it's new and it makes LOTS of difference.
I believe 2G over 1G on his box would make a lot of difference
I was just saying to your overall statement. 5 years ago I had 4 gigs of ram though.

---

### Post by ronnielsen1 on 2011-03-26
You're fortunate. I'm still maxxed out at 2G. I need a new box (without the junk embedded intel video it won't let me disable in bios)

---

### Post by bumder on 2011-03-26
So you think i should stick another 1Gb stick in?

RAM cheapest when it's new? thats like the total opposite of everything else technology wise! lol

---

### Post by cascade9 on 2011-03-26
> **Anthraxinsoup said:**
> Not trying to be a jerk here, but RAM is only really needed past 4Gigs if you are doing insane stuff. One I find a job I will go past 4gigs, but most people, and by most I mean 99% only need 4gigs. 8Gigs is just nice to have.

+1. 
Not that you can be quite so general about it even then, some people wont use 4GB currently at all. I know of several computer users who do nothing more than a browser with 2-3 tabs (or even 2-3 windows because they havent 'got', or dont like tabs), with at wost a media player working at the same time....even 2GB with win7 would be more than they 'need' ;)  

I'd still say to anbody getting a new machine (deskotp anyway) that you really should get at least 4GB now. It wont cost much more than 2GB/3GB, and well worth it if only for possible future developments.  

> **ronnielsen1 said:**
> Not sure how you're doing your math but anyway, 5 yars ago we wouldn't have imagined using the amount of ram that is used nowadays. It's cheapest when it's new and it makes LOTS of difference.

Nope, wrong, RAM is not 'cheapest when its new'. Thats totally wrong. Generally RAM pricing is cyclic, its most expensive on relaese, i gets chezaper as more people start producing it, get better at the production processes etc. It will then start to get more expensive because there is another new RAM standard coming out, production and marketing efforts move onto that. This process just repeats (Fast Page-> EDO-> SD-> DDR-> DDR2-> DDR3 (and probably coming up in the next year is the new flashy DDR4!!) .  

Here in 2002, 128MB SDRAM was $60-75, 256MB SD RAM $100-115, 512MB SD RAM $230-250. 

Now it would  be more like $30-40 for 256MB, $65-80 for 512MB...

Apart from the very rare RD-RAM, RAM prices in general have fallen huge amounts over time.  RD-RAM is the exception becuase RAMBUS went around sueing any potential fab partners so virtually nobody makes the stuff.

---

### Post by ronnielsen1 on 2011-03-26
> So you think i should stick another 1Gb stick in?

RAM cheapest when it's new? thats like the total opposite of everything else technology wise! lol

I would, with only 1G of ram. It made me a lot faster and enabled me to run better graphics and more intensive programs like VirtualBox faster.

As far as the memory argument, I may be wrong on the price going up in price as fewer companies stop making it. I know DDE 1 memory is more expensive than DDR 3 Memory. I was told that by a tech but it's entirely possible that it's a wrong statement. I guess I have to wait until 2016 and price DDR 3 memory then.

As far as your computer running ubuntu with gnome, YES you would notice a difference.

---

### Post by Artemis3 on 2011-03-26
RAM does have a fluctuation like that. Its expensive when its new, then it will slowly go down until the next generation appears, where as it starts becoming scarce the price slowly goes back up.

More memory in a netbook does have a slight disadvantage, it needs more power so the battery will be drained a little faster. A 32 bit platform should stick to 2g of RAM at most; my desktop has 8g and right now sysmon shows 16% used, 28% cached, the rest is unused. Thats with gnome/metacity, Firefox 4, amule and pidgin running, so I'd say 4g would be the sweet spot unless you run memory intensive programs such as virtualization, etc.

I don't use a swap file at all, because i don't suspend and i hate the disk thrashing involved when a swap file is really used. However, for a netbook intended to hibernate, you need a swap size 101% of your physical ram, usually not a problem unless you are on a small SSD.

Imo going from 1 to 2g is not that much of deal, it is if you had 512m. But if you go from a spinning mechanical drive to a good quality SSD (such as Intel X25), you will feel your machine faster; even a desktop using a SSD for the / partition and leaving swap and /home in the mechanical drive improves substantially.

---

### Post by bumder on 2011-03-26
Okay, been looking into it more. I only have one RAM slot in my NC10 (currently filled with 1Gb stick).

Therefore, I would have to get a 2gb stick to replace the 1Gb stick (hope that makes sense)

Best price I could find is on play.com, which is £17.99 total, for Kingston 'value' RAM.

Is this type of RAM going to be usable on other netbooks/laptops (i've read something about ddr3)?

---

### Post by ShakeyJake on 2011-03-26
A lot of new laptops are still using DDR2 ram, but I doubt you'll find too many uses for your old ram in the future. Rest assured that the Kingston is perfect for your netbook.

---


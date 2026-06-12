---
title: "Buying a new PC"
date: 2015-11-26
forum: Hardware
---

### Post by Cyber72 on 2015-11-26
My current ageing pc would  be fine but the integrated graphics mean sound and vision are out of sync on youtube. I want something that will be as future proof as possible. Some questions.

1) How can I find out if the computer will run a 128 (or even 256 bit) operating systems? I'm considering the Gigabyte F2A58M-HD2 motherboard.
2) Is dedicated graphics still much better than integrated graphics?
3) I estimate that my usage will mean each 100 Watts will cost £50 to £70 per year. I know power consumption varies any advice an motherboard / chip set. I'm looking at the NVIDIA GeForce GTX  750 Ti graphics card for low power consumption.
4) Anything else I should be taking into account?

I'm considering [http://www.ebay.co.uk/itm/151826779825?_trksid=p2055119.m1438.l2649&ssPageName=STRK%3AMEBIDX%3AIT](http://www.ebay.co.uk/itm/151826779825?_trksid=p2055119.m1438.l2649&ssPageName=STRK%3AMEBIDX%3AIT) 

Many thanks

---

### Post by TheFu on 2015-11-26
If your current system just needs a newer GPU, why not just do that and disable the onboard GPU in the BIOS? A $30 GPU should make youtube work.

There are zero plans for consumer OSes to support more than 64-bit OSes. In short, you aren't willing to spend the money; neither am I. Only specialty server OSes support more than 64-bits. Generally available servers are 64-bit for the next 10 yrs, at least.  [https://en.wikipedia.org/wiki/128-bit](https://en.wikipedia.org/wiki/128-bit)

If you game with high-end FPS-type games, then a separate GPU is important. For productivity apps and video playback, current Intel integrated GPUs are excellent. I expect the same applies to current AMD onboard-GPUs too.

If you care about power consumption, there are highly capable laptop CPUs that need less than 20W.  A fine desktop CPU will use 35W - like the Pentium G3258 - with peak use of 65W.

I always look at ports for every new system. Lots of USB3, a GigE network, and 6 SATA3 connections. Today I want to avoid any DDR4 systems and much prefer Intel over AMD for the CPU. AMD tends to require much more power for the same workload.

So.... I build systems for a specific purpose. NAS devices are different from desktops, or media servers.  For a new desktop build, I'd get the fastest Core i5/i7 I could for $200, then pick the MB to match (with the no-DDR4 restriction). DDR3 RAM is cheap. DDR4 is not.  I'm partial to Gigabyte MBs too - $100-ish is my price limit for that.  So, for $300 I get a new computer that is probably 5x faster than my last desktop (1st gen Core i5-750). 

Do you want any specific video output support? Audio?

These days almost every computer I'd get is plenty fast for my desktop needs. Heck, I've been using a Haswell Celeron for 18 months on a chromebook without any CPU speed complaints. Compare **passmark** values as a relative performance comparison and find it to be close enough for comparing different CPUs. Any CPU over 1500 is fine for common desktop things.  Passmark over 4000 is a quick CPU. Some comparisons (I own these):
```
Intel Pentium G3258 @ 3.20GHz   4,002   $59.99
Intel Celeron 2955U @ 1.40GHz   1548
Intel Core i5 750 @ 2.67GHz    3747
```

A passmark of 7600 is about $200 worth of CPU,  but it takes 84W of power. Is that amount of power really necess ary?

Update: BB wrote good info about PSUs below. Haven't used more than a 430W PSU .... ever.  Some of my systems use PicoPSUs with just 80W provided. Efficient systems these days without addon GPUs would work fine with a 180W PSU. SSDs don't require much power and even spinning HDDs use LT 5W each.  I'm partial to quiet Seasonic PSUs. Had failures from all the other "brands" over the years.

---

### Post by Bucky Ball on 2015-11-26
You can also replace the power supply if you're worried about energy consumption. Old generic silver box PSUs are unsafe and better as a heater as they run <70% efficient generally. They will cost you in the long-term. 

There are super-reliable 80 or 85+ efficiency PSUs with excellent safety switches and a lifetime longer than the new PC. PSU is the heart of the machine. Don't buy excellent bits, if you buy any at all, and then chuck in a generic silver box. When that sparks and dies they generally don't go down alone. They are quite capable of frying some or all of the other components in the box along with themselves (and they can set fire to curtains ... don't laugh, seen it happen). 

[Do a search for PSU calculators]("https://duckduckgo.com/?q=psu%20calculator") (Antec used to have a particularly good one). There are plenty around. This will give you an idea of the size you need. Another mistake I see here is people who want to check a few emails, surf the net, watch a movie, listen to music. They have a hard drive or two and integrated graphics and go throwing a 750W PSU in there. Waste of money, energy, and resources. A machine like that will happily purr along on 450W, or possibly less. A 450W 85% brand-name PSU makes the <70% 750W generic silver heater/time bomb laughable. The regular user generally doesn't need anything like that size.

PS: Never heard of a 128/256bit OS. Ubuntu certainly doesn't have one. Do you mean 32 or 64bit? That is normal and what's available. (Perhaps 256bit processors in domestic computers are a thing of the future, though.)

PPS: As for the power consumption of other bits, it is easy enough to go to the manufacturer site, locate the product, check the specs/power consumption, compare. Again, it all starts at the PSU. You can have the most energy efficient components on the planet in the box and won't make much diff if you have a PSU that is running at 70% or less efficiency. A no-brainer. If you can warm your hands during winter, replace. With an efficient PSU matched to your components you should be able to put your hand on the PSU vent at the back of the machine with no discomfort after it's been on for an hour or two.

And thus ends another of my rants about the advantages of energy efficient PSUs! ;)

Good luck. :D

---


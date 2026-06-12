---
title: "Need a new MoBo/CPU.  Recommendations?"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by gregfi on 2007-01-26
My current setup, which has served me well for ~5 or 6 years now, is intermittently powering off.  It began gradually, but now my mean uptime is probably around 10 minutes.  I tried swapping out the power supply and the power strip (neither of which helped), and the fans are still happily spinning (so I don't think it's a heat issue), so I'm left believing it's a weird motherboard component failure.  Anyway...

I'm in the market for some new low-level components (CPU, Motherboard, Memory).  Reading around, it seems like the new x86-64 cpus and their associated motherboard chipsets are less than hassle-free.  nForce4 seems to dominate the AMD chipset market, but I'm not sure how comfortable I am having proprietary drivers interfacing with low-level stuff (I hear bad things about the nForce 2 driver experience).  

I haven't followed this stuff for such a long time, but it used to be that AMDs were the de-facto best deal in town.  I'm looking for low price, low effort, and stability.  I don't play games, I don't need the best performance.  Can someone offer some recommendations?  

As an aside, if I just toss a new motherboard and CPU in there, is Edgy smart enough to figure it out and make the necessary changes?

Thanks!

Greg

---

### Post by mrojas73 on 2007-01-27
If you plan to run Edgy here is what I can not recommend so far:

Abit AB9
Asus P5W Deluxe.

I already have an Intel Core2Duo 6400 so I have to stick with 775 boards and so far the two I mentioned work ok with Daper, but now on Edgy.

I my try a 945 chipset next.

---

### Post by futz on 2007-01-27
> **gregfi said:**
> My current setup, which has served me well for ~5 or 6 years now, is intermittently powering off.  It began gradually, but now my mean uptime is probably around 10 minutes. 
Did you try reseating ram, cpu, video card and other pci cards (I know, unlikely to help, but...)?

With a machine 5 or 6 years old (antique), and you wanting to put in a new mainboard/cpu, you're also going to have to upgrade the ram and video card (new mainboards don't use AGP anymore - pretty much all PCI-E now).  Also you'll almost certainly have to buy a new power supply.

How many hard drives and opticals? All IDE? Many new mainboards are moving to just a single IDE channel and the rest SATA. A single IDE channel supports two IDE devices. If you've got too many IDE devices, you may have to replace some with modern SATA parts.

> less than hassle-free.  nForce4 seems to dominate the AMD chipset market, but I'm not sure how comfortable I am having proprietary drivers interfacing with low-level stuff (I hear bad things about the nForce 2 driver experience). 
nForce2 was a long time ago - can you even buy mainboards with that anymore?. The new nForce stuff is fine. I have a couple. No problems.

King of the hill now is the Intel Core 2 Duo CPU line with either intel 965/975 or nforce 650/680 (and some other 6x0 numbers) chipsets. Tons of bang for the buck.

But if you want less expensive and good enough, AMD Athlon 64's (the X2 dual-cores too) are pretty good. The stores need to move them out or be stuck with em. They can't keep up with the new Intels, but not too bad.

> As an aside, if I just toss a new motherboard and CPU in there, is Edgy smart enough to figure it out and make the necessary changes?
Maybe (probably not), but I'd sure back up everything important and be ready to do a full reinstall.

---

### Post by gregfi on 2007-01-27
Thanks, futz.

Yeah, I had counted on upgrading the RAM, but the video card and SATA were news to me.  

What's a sufficiently powerful power supply these days?  I thought there was starting to be emphasis on having this stuff consume *less* power and not more.

---

### Post by futz on 2007-01-27
> **gregfi said:**
> Yeah, I had counted on upgrading the RAM, but the video card and SATA were news to me.
I was generalizing a bit about boards having only a single channel of IDE. There ARE boards with two or more channels still, but they're disappearing fast. IDE is going away.

You can even still find a few rare boards with AGP slots, but you really severely limit your choices if you want AGP these days. PCI-E is the norm.
> What's a sufficiently powerful power supply these days?  I thought there was starting to be emphasis on having this stuff consume *less* power and not more.
I wouldn't waste my time with anything less than 450W. Sure you might not need it all, but if your component's don't need it all they don't draw it all. And if you start adding stuff you don't have to upgrade again. The newer video cards (the bigger ones, anyway) draw a lot of juice. Many have their own 6-pin power connector for a dedicated supply, as the PCI-E slot can't supply enough to run them.

Do buy a quality name-brand PSU like for instance Enermax, OCZ, Antec or several others. No-namers have a tendency to have very short warranties, fail early and not actually put out what they're rated for.

---

### Post by laidback on 2007-01-28
This site may help for the video card choice. I've read that Nvidia is best for Linux but as I only use standard VGA with no 3D or gaming I cannot comment on the suitability of them. I run 1280x1024 from an old ati 2x AGP, I'm happy. 

I agree with the comment above about power supplies, especially the rating; 450W seems to be the starting point today.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

### Post by breakaway on 2007-01-28
If your system is randomly shutting down, its probably due to an overheating CPU, and the system's shutting itself down to prevent any permanent damage. What you need to do is clean off the current thermal paste, and apply new paste. I recommend Arctic Silver.

---


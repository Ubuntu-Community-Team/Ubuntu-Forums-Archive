---
title: "Linux Compatible Hardware"
date: 2017-07-04
forum: Hardware
---

### Post by daniell59 on 2017-07-04
After 10 years it is now time for me to build a new computer. Since I will be using ubuntu most of the time, I want hardware that is compatible.
I was thinking of the AMD Ryzen, but have read of compatibility issues. Since I do not do gaming, speed is not an issue. Would i experience less problems going with Intel?
Any suggestions will be appreciated.

Thanks

---

### Post by slickymaster on 2017-07-04
Did you already went through [this sticky]("https://ubuntuforums.org/showthread.php?t=361236")?

---

### Post by Bucky Ball on 2017-07-04
The best place to start is by writing down exactly what you are going to do with the computer and working from there. Waste of time building a mega-box if all you're doing is surfing the net and listening to music. Do you need a separate GPU or will one that comes as part of the motherboard be fine (usually Intel)? What are the other specs you are using, e.g. processor? Amount of RAM?

If you're not gaming and not doing video production you may get away with whatever graphics chip your motherboard comes with. Unless expense is no issue, and perhaps even then, you don't want to be buying hardware you don't need. ;)

---

### Post by oldfred on 2017-07-04
I liked using partpicker.
It did save me from buying wrong size hard drive for my smaller case. It needed laptop size not standard.

But using SFF size case & power supply was more expensive than standard sizes. But where I have PC I do not have a lot of room, but did not want laptop.

 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

### Post by daniell59 on 2017-07-04
It has been a long time since I built a computer. I am now considering an Intel board and processor. The board and the processor both have video. How do I deal with that? Will I need a separate video card?

---

### Post by CatKiller on 2017-07-04
> **daniell59 said:**
> It has been a long time since I built a computer. I am now considering an Intel board and processor. The board and the processor both have video. How do I deal with that? 

The motherboard doesn't have video, it just enables the video built into the processor.  Intel graphics are generally well-supported by the open source drivers built into the computer.

> Will I need a separate video card?

It depends on what you want to use the computer for.

---

### Post by daniell59 on 2017-07-04
I have been looking at the solid state drives. i did not realize that they were so expensive.

---

### Post by oldfred on 2017-07-04
If you want the very new NVMe drives they are more expensive, but very fast, and use the M.2 form factor. But all M.2 SSD are not NVMe, mine is standard SATA.
But with Ubuntu you only need a smaller SSD as boot drive and then a larger HDD for data.
And SSD have dropped a lot.

I did use a M.2 SSD on my build and 250GB was not that much more. But first SSD was only 64GB and I had two installs of Ubuntu on SSD in30GB / (root) partitions and all my data in /mnt/data and other partitions on HDD.
With M.2 you have to check what size (length like 2280) Motherboard supports.
[https://en.wikipedia.org/wiki/M.2](https://en.wikipedia.org/wiki/M.2)

---

### Post by CatKiller on 2017-07-04
I believe SSD prices have been high (comparatively) because of supply-line issues, similar to the hard drive price spike caused by the flooding in Asia some years back. Hopefully they'll come down again. As oldfred says, they have already come down massively in price from when they were first released.

Again, as oldfred says, installing onto an SSD and having your bulk data on a slower HDD is perfectly fine. That's how my desktop is set up. You don't necessarily need to get an SSD large enough to hold *everything*.

---


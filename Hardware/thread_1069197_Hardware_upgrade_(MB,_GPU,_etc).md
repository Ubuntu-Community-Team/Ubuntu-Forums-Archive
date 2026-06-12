---
title: "Hardware upgrade (MB, GPU, etc)"
date: 2009-02-13
forum: Hardware
---

### Post by linfidel on 2009-02-13
Hi, all,

I've been using an old ABit NF8 series MB (Athlon-64 3000+), with 1 GB, and a cheap AGP video card (GeForce FX 5200).  Performance is not bad for what I do (no gaming, mainly programming and internet).  I think I could use more memory and speed for Eclipse, though.  But I don't want to spend too much, under $500 for sure - I'm not working right now.

I was looking at the Gigabyte GA-EP45-UD3R (or L?) at Egghead for $110, which seems like a nice MB.  Has lots of USB, SATA, and an IDE channel for my existing DVD and spare backup drive.

One thing I'd like is the ability to boot from USB thumbdrives, which none of my current beasts seem to do.  Also, I'd like one that will go into standby mode without crashing like my abit.

So, I'd like feedback from any owners of the Gigabyte MB, or suggestions for something similarly priced with the features I mentioned.

Also, assuming I don't get a different one with onboard video, I'd appreciate some suggestions for video cards that will handle Compiz effects, and perhaps dual monitors, although I don't have that now. Mainly, I don't need super-speed, and my old NVidia cards would be fine except they are AGP and the new motherboards mostly don't support them.

Thanks for any suggestions.

---

### Post by vacc73 on 2009-03-16
Hello;

I have been looking as well and I have noticed that gigabyte in their specs, suggest that those of us enlightened enough to use linux need to go to the chipset or third party vendors to download drivers.Amd has not got back to me yet about their chipsets and how they are with linux, but the cpu's obviously are ok. I have also had good results with nvidia products. It would seem that from my own research so far, if you stick with amd or nvidia chipsets on your board you'll be alright.
Currrently I am using a winfast/foxconn board right now and the only reason I took a chance on it(Foxconn apparently does not like linux) is aside from price, it has a nvidia chipset.So far it works fine with an Athlon64 3800 and 4 gigs ram on Intrepid.
Hope all goes well and please post the results:popcorn:

---

### Post by Cracauer on 2009-03-16
You should like to the products you want to buy.

Figuring from the name, is that using the 945 chipset? If so -> trash.

---

### Post by markbuntu on 2009-03-16
People have some weird problems with some gigabyte mobos. Make absolutely sure that that particular board works with Ubuntu before you buy it, like someone saying they have it and it works for them.

---

### Post by linfidel on 2009-03-16
> **Cracauer said:**
> You should like to the products you want to buy.

Figuring from the name, is that using the 945 chipset? If so -> trash.
GA-EP45-UD3R, info from Wikipedia:
**GA** - Gigabyte
**E** - (Dynamic Energy Saver) - Energy saving features
**P45** = Intel P45 Chipset
**UD** (Ultra Durable 3) - Introduces 2 ounces of copper for both the Power and Ground layers.
**R** - 2 extra SATAII ports and possibly RAID support. No FireWire ports. No ATI CrossFire support.
or
**L** - Probably "Lite". Less SATAII ports. No RAID support. No FireWire ports. No ATI CrossFire support. Heatsink cooling

---

### Post by linfidel on 2009-03-16
I've decided to save the money for now, and make due with my old system.  I'm not working right now, so I really shouldn't spend too much money.  

I reinstalled Ubuntu on a clean partition, and it's actually working better now.  Previously, I had overwritten the main OS, but kept my /home directory.  This time, I replaced all, then mounted my previous /home directory so I could copy or import some of my application data, like Thunderbird, Tomboy notes, and documents.

I haven't installed Compiz or the proprietary NVidia drivers so far.  I may want to just keep it simple.

---

### Post by mpsii on 2009-03-16
Dell has "entry level" desktops under $500... I use the quotes because they come with 2GB of RAM, DVD burners, and 350GB hard drives.

[http://www.dell.com/home/desktops?~ck=mn](http://www.dell.com/home/desktops?~ck=mn)

---

### Post by linfidel on 2009-03-17
> **mpsii said:**
> Dell has "entry level" desktops under $500... I use the quotes because they come with 2GB of RAM, DVD burners, and 350GB hard drives.

[http://www.dell.com/home/desktops?~ck=mn]("http://www.dell.com/home/desktops?%7Eck=mn")
I considered that possibility, and looked at some prebuilt desktops; for most people, that would be the way to go, but I've never bought a full system like that.  I always have enough parts to build cheaper.  For $500, I'd have a much nicer system, although if I were to need to sell it, the Dell would probably be worth more to most people.

---

### Post by Cracauer on 2009-03-17
The P45 (not 945) chipset is a piece of junk.

So will be the boards in the cheap Dells. Dells tend to be pretty solid overall, though, with decent cooling and PSUs.

There's no reason to say that Gigabyte might be less Linux-friendly. The chipset is the same. Problems come in when the mainboard chipset misses PATA or Ethernet and/or PATA or Ethernet come from third-party chips. You get around this by buying mainboards with decent chipsets. If not, Gigabyte is definitely not worse than other vendors in picking stupid additional chips.

---


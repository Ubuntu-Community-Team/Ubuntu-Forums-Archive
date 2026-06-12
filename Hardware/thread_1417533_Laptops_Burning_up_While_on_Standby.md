---
title: "Laptops Burning up While on Standby"
date: 2010-02-27
forum: Hardware
---

### Post by foresthill on 2010-02-27
I have this problem with two different laptops running 9.10.

When I'm using the laptop during the day, the temperatures seem reasonable, and the fan hardy ever comes on. But when i close the lid at night and the screen turns off, the temperatures skyrocket. I get 4-5 times more heat (sorry but I don't have a temp monitoring program installed) while "sleeping" than is generated while the notebook is actually being used. This makes absolutely no sense to me.

The palm rest and the bottom of the computer are actually hot to the touch (not merely "warm").

I'm not naive enough to expect a solution, heck I'll be lucky if I get a single response to this thread. I'm just wondering if this is happening to anyone else.

Because if it is, this seems like a very serious problem that ought to be brought to the attention to the devs so that tens or hundreds of thousands of laptops don't die prematurely because of some "endless loop" of some sort that occurs during sleep, which might possibly be preventable through some sort of patch.

---

### Post by IcarusR on 2010-02-27
What laptop is this ??

No ideas apart from the obvious ... switch it off at night.

---

### Post by 1337 on 2010-02-27
First of all you should type here exact model of your laptop, we are not prophets we dunno what machine you use. Secondly you should check launchpad.net bugs category if people reported some overheating problems on similar laptop models. I personally don't believe it can be a software bug, Linux usually support laptops very good in terms of power management so no heat problems should be encounter. Another thing is laptop care, you could by yourself a can of compressed air (should be avail in every electric/computer store or a market). You should locate on your laptop a masking bay closely to the fan, unscrew it and use a short bursts of compressed air to get dust out of the fan, that should generally help with every overheating problem. This should be done at least every year and if you are a smoker more often. Good luck.

---

### Post by wilee-nilee on 2010-02-27
My acer aspire netbook inspite of using the gconf-editor to reset the lid to do nothing goes to 100% cpu when I close it, I suspect this is happening to you. It is obvious to me as I have my computer plugged into a monitor. 

So you might check this out on your computer.

---

### Post by foresthill on 2010-02-27
I believe that's what's happening to me, judging by all the heat.

FWIW the same thing happens on two very different laptops. One is a Gateway MX 6441 with an Athlon 64 bit 1.8 Ghz processor I bought in 2006. It has  ATI 200M integrated graphics, a Hitachi 80gb 7200 RPM hard driver and 1.5 gigs of RAM. I'm running 32 bit Ubuntu 9.10

The other laptop is Gateway NV78 with an Intel Core 2 Duo system with Intel 4500 series graphics, 4 gigs of RAM and a 500 GB Toshiba hard driver. I'm running 64 bit Ubuntu 9.10 on that laptop.

I'm having the same problem on both systems.

That's the reason I didn't mention the hardware, because it's so different on the two that I think hardware can safely be eliminated as a factor.

So what appears to me to be happening is that the CPU's on both systems are getting maxed out somehow. And there is absolutely no reason for this to be happening on a system that's supposed to be on standby. And if that's what's happening, no amount of cooling will solve such a problem, and the life of the affected hardware is going to be shortened SIGNIFICANTLY. 

I think this is a huge problem and hope someone is looking into it, and am surprised that there aren't more people having this same problem.

---

### Post by His on 2010-03-06
do a search on launchpad.net and see if a bug has already been reported. I found a bug reported for my laptop.

---


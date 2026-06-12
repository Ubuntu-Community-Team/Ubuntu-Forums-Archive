---
title: "How to fix crashing computer!"
date: 2008-07-22
forum: Hardware
---

### Post by groundnut on 2008-07-22
In the past my pentium4 computer crashed many times during 3d rendering with Blender. Now it also crashed during compiling.

How to solve this problem?

---

### Post by Potatoj316 on 2008-07-22
It might be a lack of ram/swap space, how much ram and how much swap do you have?  Also do you have a video card, and what are you compiling? (is the program big or more like a hello world)

---

### Post by groundnut on 2008-07-22
Thanks Potatoj316,

I think it's a hardware problem, because this problem was already present with Windows XP, before I installed Ubuntu.

I don't now how large the SWAP is. I can't find it in places and I don't know how to do it with the command line. Though I would like to know.

The RAM is 512 MB.
It's an ATI video card.

I'am compiling the Gimp Animation Package (GAP), which is a animation plugin for the Gimp.

I've done this compilation already for my other Linux computer (Xubuntu, Pentium 3). No problem.

kind regards,
Tony

---

### Post by ljonesj on 2008-07-22
i may be wrong but it might be and issue with the ati graphics card

---

### Post by groundnut on 2008-07-23
Hello ljonesj,

Why do you think it might be an issue with the ATI video card?

---

### Post by Growbag on 2008-07-23
I would suggest checking your hardware, it's a long and potentially expensive path, but if your hardware is dodgy, everything software won't work properly.


A few suggestions:

1. Power supply, is it overheating/too low powered/faulty capacitors (don't open it unless you are adept with electricity and high voltages though!!).

2. Capacitors on the mainboard, if they look rounded or "funny" on the top of a few, especially around the CPU, you need to replace them, or get a new mainboard.

3. RAM, take half out (if you have 2 or more chips), swap them around, try another chip (or set).

4. Hard disk, do a complete surface scan, try using an old disk see if that helps.

5. Try another (cheap) video card.

6. Try doing it from a liveCD with another distro, you never know your luck.

7. Check the BIOS settings for your mainboard, maybe set them to default.

8. Check the cooling fan on the CPU, clean it and make sure you are getting a good airflow through the box.


Good luck!

---

### Post by Yannick Le Saint kyncani on 2008-07-23
You can test your ram with memtest86+.

---

### Post by groundnut on 2008-07-23
thanks,

I have installed the lm-sensors sensors-applet.
It measures 4 temperatures. One of them is too high (73 degr. C) while at a pretty idle state. 
This indicates that a too high temperature of the CPU is the culprit.

kind regards,
Tony

---

### Post by Growbag on 2008-07-24
I would guess at CPU on that one :).

A new cooler/fan should be quite cheap.

If you have a house fan, you could take the lid off the computer and point the fan at it, see if that makes a difference until you manage to get a new one :).

---

### Post by groundnut on 2008-07-24
Thanks Growbag,

Don't you think applying some new thermal compound would be sufficient?

By a cooler do you mean a heatsink?

kind regards,
Tony

---

### Post by evets25 on 2008-07-24
He's talking about that thing that sits on your CPU and cools it. It can be a heatsink, a fan, or a heatsink and a fan. Usually there is thermal glue involved somehow. It usually looks something like [this]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2943299&CatId=493"). If you're putting on a new one, you *NEED* thermal glue. This goes between the heatsink and the top of the CPU itself. I would recommend a new one, since they are really really cheap, just make sure you get one that works on a P4. (any of the generic ones should do)

---

### Post by groundnut on 2008-07-24
Thanks evets25,

Is mentioning socket 478 enough information for a person at the computer shop to sell me the right cooler /fan combination

kind regards,
Tony

---

### Post by Growbag on 2008-07-25
> **groundnut said:**
> Thanks Growbag,

Don't you think applying some new thermal compound would be sufficient

Possibly, but make sure the fan and heat sink are clean and free of dust, also make sure the fan is actually spinning :).  It does have a fan doesn't it?  If not, then get one with a fan, the Intel ones are better quality.

> By a cooler do you mean a heatsink?

Yes, well the whole unit, fan AND heatsink, they usually come as a single unit.  But some proprietary machines like Compaq/IBM etc' have some rather odd arrangements, like a big Aluminium heatsink block on top of the CPU, and a cowl and fan sitting off to the side, or attached to the case side.

Another thing to look out for is if the heatsink is sitting on top of the CPU properly.

I've seen that problem many times, sometimes the components near the CPU prevent the heatsink from sitting level, and I also made that same mistake myself, and blew up an expensive AMD 1800 CPU (they were expensive once!).

SO if you clean the old compound off and put new stuff on, make sure the heatsink block is sitting level.


> Is mentioning socket 478 enough information for a person at the computer shop to sell me the right cooler /fan combination

It should be, or simply ask for a cooler for a P4.

If they don't know what you mean, walk out and find a place that does!  Unfortunately they might be a bit hard to find these days, ebay might be your last hope.


Good luck :).

---

### Post by groundnut on 2008-07-25
Thanks again Growbag,

I've been able to remove the cooler today. There is hardly any thermal compound left. So I think the lack of thermal compound is the culprit.
Tomorrow I am going to buy thermal compound. I will try that first. If that's not enough I will escalate to the next step: the cooler.

The dust has already been removed. I will clean the heatsink tomorrow.
Yes it does have a fan. It's an Intel fan.

I will make sure that the heatsink block is at sitting level.

kind regards,
Tony

---

### Post by groundnut on 2008-07-26
Problem fixed!

Both rendering and compiling is now ok.

---

### Post by ljonesj on 2008-07-26
sorry to get back so late on this glad u got it fixed i said the ati graphics card could have been a culprit as ati cards are not that great with the linux os's at the moment

---

### Post by groundnut on 2008-07-27
thanks ljonesj,

This Ubuntu pc used to be an Windows XP computer one or two month ago. Back then it had the same crashing problems.

---

### Post by Growbag on 2008-07-27
Glad to hear you got it sorted groundnut.

I've seen many systems in my time with similar problems.

The worst being the "tilted" cooling block, where the builder had got one edge caught on the CPU socket and it wasn't seated properly.

The machine was unreliable from the start, and nobody in 5 years could figure out why it was so unstable.  And by the time it got to me it was too old anyway!

We live and learn :).

PS.  Just for a laugh, I attached a picture of a CPU cooler I saw in a computer shop window the other day.  It was so big I was amazed.  It looked like a lawnmower engine, and just as big!

---


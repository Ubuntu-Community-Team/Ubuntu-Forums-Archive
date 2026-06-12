---
title: "Upgrading to multi-core from a 939 pin 3500+"
date: 2009-04-27
forum: Hardware
---

### Post by student2501 on 2009-04-27
This computer uses:
Ubuntu 9.04 64 bit

Current specs include
|| AMD Athlon 64 Processor 3500+
|| ASUS A8N5X ACPI BIOS Revision 0902
|| 2x512MB DDR333 (dual channel mode)
|| Nvidia 7300 GT

939 dual core chips are expensive and hard to find. It almost seems pointless to update this outdated system. I'll edit the posting to reflect what I'm currently looking at. Here is the list...
[B]
1. new chip[/B]
Intel Pentium E5200 "Wolfdale"
2.5GHz | 800 Mhz FSB | 2MB L2 Cache | LGA 775 | 65W | Dual-Core | 45 nm
$69.99 + free shipping @ newegg.com
[http://www.newegg.com/Product/Produc...tel-_-19116072]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116072&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Processors+-+Desktops-_-Intel-_-19116072")

**2. new motherboard**
I'm overwhelmed by the options out there - Looking for something I can overclock that Wolfdale past 3Ghz and will work with Linux no problems. Stability and driver compatibility also are a must.

**3. new memory**
(4 GBs at the least - I always disable swap)

**4. new power supply**
(going to put the old one in another system)

I want my new system to be able to handle multi-tasking like a hot knife through butter. Looking for suggestions from other Linux users who have taken the path to multi-core already. From upgrade to upgrade the time frame is usually a solid 5 years. I'd like to do it right the first time. Which would be the better route to go? AMD or Intel? I am not a gamer. Thank you in advance.

---

### Post by jerrrys on 2009-04-28
Which would be the better route to go? AMD or Intel? Thank you in advance.

cant believe nobody answered this...both are great...or at least as good
as the operator....

---

### Post by student2501 on 2009-04-29
> cant believe nobody answered this...both are great...or at least as good
as the operator....That does not help any... :/


Both Intel and AMD are good options depending on what you get.  All things being equal I'm looking for the following...

1. a very fast, solid, and reliable platform with
2. the ability to easily overclock
3. naturally it has to have no problems with linux

---

### Post by jerrrys on 2009-04-30
still no reply,except me...bummer dude...

well, there's 1100+ members on line right now, so as far as your last post goes.

i dont run dual core, but i run dual processors...3gig clock ea...and since their 'xeon' i have hyper-threading engaged which means my computer sees 4 physical processors...oh yes 1gig of L2 between the two and a 533 FSB...and for the most part everything happens in a blink of an eye...my wife has a more powerful system, but it cant keep up with mine...she runs vista; i run linux...any help? probably not...but you got a bump out of this...

---

### Post by student2501 on 2009-04-30
Yup - Visita will slow any computer down because it was designed to.  :popcorn:
Now this is a true story... My sister's laptop would not load properly after one of Vista's updates and she wanted to salvage her pictures and movies because she had no backup solution... the restore point software failed and I had no equipment to work on a laptop.  Nothing else would work without formating the entire drive or paying someone else to do it.  In the end I found a solution - accessing the drive with a LIVE CD of Ubuntu!  I was able to save all her pictures and do a fresh install of Vista on her system.  =]

---

### Post by kspncr on 2009-05-01
I don't know about Linux compatibility for any of this stuff (I don't use Ubuntu on my gaming PC) but in general I'd go with an AMD over an Intel processor. Sure, Intel's i7 is the most powerful processor on the market today--there's no denying that--but who really has the money for one? And like you said, you're not a gamer so there's no need for you to have something that's so overkill. So in terms of mid-range dual-core processors, I think the AMD and Intel processors perform about the same, but the AMDs are cheaper. Just out of curiosity, why do you feel the need to overclock?

I was seriously considering upgrading my motherboard to this [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128387](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128387)  largely because it supports AM2, AM2+ and AM3 sockets types. Won't need to upgrade that bad boy for a long time. The reviews say that it overclocks well, but I never overclock (I don't see the need) so I can't comment on that. There's also at least one review that says this MB works great with Linux, however he doesn't specify which distribution he used.

As for power supplies, I've always had success with Corsair (just upgraded to a new one a few weeks ago, love it). I'm not sure what your PC's usage is going to be like, but since you said you don't game, I think 500 watts is probably the most you'd need so I'd be looking at something like this [http://www.newegg.com/Product/Product.aspx?Item=N82E16817139003](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139003)

I'm also unsure of your budget so sorry if I suggested anything out of your range. Hope any of this helps.

EDIT: I forgot to mention that you can check my processor in my signature, which is known to work well with Debian, so there's a fair chance it would work with Jaunty.

---

### Post by student2501 on 2009-05-01
You def. go a different path than most others for sure... Everyone seems to be pushing those Core 2 Duos and another thing also got my attention.  That you run Debian on your flagship computer while running Ubuntu on your laptop.  I usually do the reverse and call upon Debian w/Fluxbox if it is a really slow computer such as a P2 or even a P1.  BTW I know it took forever +1 day but Debian 5 is out.  I always go with the text based install discs because they are less headache.

So what is it about the AMD side that makes it worth my while?  I see you go on the side of stability however overclocking is fun.  Think of it as an added bonus to whatever cpu one gets - Ofc one must take it slow to ensure stability - with a little patience and slowly increasing speeds and testing it with programs such as superpi (at the minimum) one can obtain higher clock speeds with confidence.  Not all processors are cut the same way and the luck of the draw will determine how far you can push it.  Some chips are just made with less defects than others.

---

### Post by kspncr on 2009-05-01
Well, I would have Debian on both my computers (my favorite distro, shh...don't tell anyone on the forums) but it was a bit of a pain to get my wireless working on my laptop so I just installed Ubuntu and it worked "out of the box." I guess it's a little strange, but there's a reason for it. I should update my signature because I am running Lenny, it just doesn't say so...

What I dislike about overclocking isn't even entirely stability (that too), I just don't like the idea of voiding my warranty, especially when my processor already gets the job done without overclocking :)

I'm a pretty cheap guy, so for me the deciding factor between AMD and Intel is price, since they perform about the same. I also think that Core 2 Duos are great (Core 2 Extremes are awesome) but I think that AMD has equally well-performing CPU that tend to cost less. That's pretty much the only reason.

---

### Post by student2501 on 2009-05-01
BTW how do you like Lenny over Etch?  Its been a long time for me and I ran out of blank discs to burn for now.

---


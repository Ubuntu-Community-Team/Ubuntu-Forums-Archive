---
title: "Fujitsu v6505 CPU Upgrade - Socket issues"
date: 2018-07-01
forum: Hardware
---

### Post by hypixus on 2018-07-01
Hi,

I'm new here and noticed a question of this format appeared here before. So, there it goes:

I own a Fujitsu V6505 laptop with Intel T5800 as its processor. I want to upgrade it with model
T9600. All parameters seem to be identical, aside from voltage and socket. My current processor,
as the official Intel Ark website says, has PGA478 socket, whilst the newer one has PPGA478.
To make things even more funny, I dismounted my current one to make photo of the socket
and after counting a few times in a row... It has 479 pins, what would suggest its incompatible
with both of them.
Is this upgrade going to work on that socket? If not, what is the best c2d processor that will
work with it?

Thanks for help! :)

---

### Post by Yellow Pasque on 2018-07-01
Supposedly, the T5800 is a Socket P chip, not to be confused with Socket M.
[https://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Core_2_Duo_2](https://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Core_2_Duo_2)
[https://en.wikipedia.org/wiki/Socket_P](https://en.wikipedia.org/wiki/Socket_P)
[https://en.wikipedia.org/wiki/Socket_M](https://en.wikipedia.org/wiki/Socket_M)

> Is this upgrade going to work on that socket?
That's a question best answered by the manufacturer, so check Fujitsu's support page for your model (I couldn't find it).
They appear to both be Socket P parts, but the BIOS has to support it, so upgrade your BIOS while you still have the old CPU in. The T9600 uses a half-multiplier and has a faster FSB than your current CPU (1066 as opposed to 800), so it may not work or may not work up to full potential. The T9500 would be a safer bet, but there's still no guarantee unless you find a list of officially supported CPU.

---

### Post by hypixus on 2018-07-01
I have latest(1.22 released on 11/08/2009) version of BIOS already for 8 years :D
FSB 1066, 800 and 667 is ought to be supported properly by my chipset(Intel GM45 I supppose, found some "82GM45" part on my motherboard near processor) as well as both processors mentioned, but **I'm not exactly sure whether chipset's list of compatible processors is good to depend on.**
[http://www.cpu-upgrade.com/mb-Intel_(chipsets)/GM45_Express.html](http://www.cpu-upgrade.com/mb-Intel_(chipsets)/GM45_Express.html)
 A list of **officially** supported CPU's **does not exist** - aside from datasheet contaning possible variants of this device.
My general idea is to upgrade current processing power to acceptable level for daily use - like browsing web or playing 00's games.

First idea of mine was to put a quad core in it, but I noticed **TDP is 10 W higher** than every c2d mobile and people mentioned many times that BIOS has to support it. I made an Excel sheet containing all Intel Core 2 processors using data from Wikipedia and found out that series T9XXX is the safest choice with power usage characteristics.
Looking on the market, T9900 (best model) is 50$, while the T9600, having just 0.2 GHz less, is for just $10 when buying a new one.

So, what's the issue with the half-multiplier? Sorry, I'm familiar with IT stuff, but never had to mess with hardware under it.
And the most important part for me - is the generation of the processor important in this case? T5800 is a Merom, while all T9xxx are Penryn.

---

### Post by Yellow Pasque on 2018-07-01
No, the chipset list is not the best. The BIOS still has to recognize the CPU and set the FSB/multiplier correctly. I doubt anyone can give you a definitive answer here. While it looks like it **should** work (same socket and GM45 supports 1066FSB), there's no guarantee.

The most encouraging thing I see is that the BIOS Changelog mentions CPUID 1067A: 
```
update CPUID 1067A BUCODE from A04 to A07
```
The T9600 and other Penryns use CPUID 1067A: [http://www.cpu-world.com/cgi-bin/CPUID.pl?CPUID=60314](http://www.cpu-world.com/cgi-bin/CPUID.pl?CPUID=60314)

> And the most important part for me - is the generation of the processor important in this case? T5800 is a Merom, while all T9xxx are Penryn.
It could be. Again, it comes down to your BIOS supporting Penryn or not. 

> So, what's the issue with the half-multiplier?
IIRC, some BIOS didn't like CPU's with them while still being able to run upgraded CPU's with whole multipliers. It might have been back in the AMD Socket AM2 days, which was many years (and many, many beers) ago for me, so don't quote me on it.

---


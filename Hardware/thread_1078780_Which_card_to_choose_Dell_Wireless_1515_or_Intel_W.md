---
title: "Which card to choose: Dell Wireless 1515 or Intel Wifi 5100?"
date: 2009-02-23
forum: Hardware
---

### Post by remiprev on 2009-02-23
Hello all,

I'm thinking about buying a Dell laptop, an Inspiron 1545. I know some people got Wifi issues, but some people haven't. So, I'd like to know which Wifi card is the best to use with Ubuntu? Do both have good Linux drivers?

[LIST]
[*]Dell Wireless 1515 802.11 Wireless-N Mini-card **OR**
[*]Intel WiFi Link 5100 802.11 Wireless-N Mini Card
[/LIST]

Thank you!

---

### Post by novafluxx on 2009-02-23
I'd go with the Intel because we KNOW it will probably work. I'm not sure who Dell licenses their wireless cards from, probably Broadcom!

---

### Post by Squid Spectre on 2009-02-23
I have an Intel 5100 AGN, works well and right of the box to boot. Reasonibly stable and really sensitive, a decent wireless card all around.

If I were you I'd see if I could dig up technical info on the Dell. Specifically you should focus on the intenal antenna array, the intel has a 1x2 (recieve/send) that allows up to 350 Mbps theoritcal transfer but because it only has 1 recieve is prone to loosing its connection from time to time. If the Dell has, say, a 3x3 array which is more common in newer or higher end wireless cards it boosts the bandwidth up to 400 Mbps and is considerably more stable for obvious reasons.

Truth be told though you'll probably never utilize the 350 Mbps that the intel is limited to but the stability from a more capable array is really useful if you live in a high noise area, like me.

---

### Post by AnybodyM on 2009-04-12
The DELL 1515n is Atheros based, and Atheros has generally very good Linux support.

Also, the Intel 5100 is a cut-down version of the 5300 and is taking very serious performance hits from the missing antenna.

The 5100 does work fine in Linux though. Performance would probably be a lot better with the 1515 Atheros or the 5300 Intel.

---

### Post by Jonathan_m84 on 2009-08-17
Two of my home-mates have the dell wifi card and I have the intel 5100 card... mine works much better (also with linux, works right out of the box).. .they have some problems with their dell card so i suggest choosing the Intel over the dell.

---

### Post by nightalon on 2011-03-30
**So I've done a little bit of digging on the subject.  Here's my run-down of full- and half-height MiniPCI-E WIFI Cards:**

*(I would have posted this in NotebookReviews, but the threads were closed.)*

_Intel:_
The Intel 5xxx cards will probably get you the best speeds; Intel made vast improvements from the days of the 3xxx and 4xxx cards.  Allegedly some of these cards only work well with Intel chipsets...I read that they do not work well with Nvidia chipsets.  I don't know about ATI/AMD chipsets; that requires further research.

Intel makes the only half-height 3-antenna (theoretically 450 MBps-capable) module.

Intel's Linux drivers are open-source, and heavily Intel-contributed.

Intel's WIFI chipsets do not work under MacOS.


_Broadcom:_
To my knowledge, Broadcom doesn't make any 3-antenna models if they ever did.  That said, the BCM94322-based chips out-perform the AR9280-based chips.  Therefore, Broadcom is the winner in the non-Intel (therefore also non-3-antenna), half-height category.

Under Linux you will need to disable power-management (in recent version of Ubuntu) to get a stable connection.  There are numerous threads on how to do this.  You add a startup script using ifconfig or iwconfig power off.  Once you have done this, performance is equal to Windows or Linux with low ping times.

The Broadcom is also the performance winner in the half-height category in MacOS.


_Atheros:_
I used to love Atheros, because I thought they were the smaller competitor and they had frequent driver updates.  They also made the venerable full-height AR5008 and AR5008X chipsets which seemed to work best of all the competition in Windows.  They were also the first 3-antenna cards when Intel was still making junk.  (unreliable connections and glacial driver/feature support)

However, for whatever reasons, the AR9280 is outperformed by Broadcom's competition in Windows, Mac, and Linux.  I'm not really sure why.

I have a full-height AR9380, which Apple seems to be using on new Mac Pros, so I'll have to test that one out as well.

Atheros cards use the open-source ath9k driver these days.

Atheros allows for promiscuous mode (at least on Mac and Windows), whereas Broadcom does not (at least on Mac).  This is of limited use to me, anyway, but indicative of why hackers like Atheros.


_RaLink and Realtek:_
These guys make budget cards.  That said, RaLink has improved by leaps and bounds since entering the industry a few years ago.  Their Linux support is much improved, although I think they only support a proprietary STA driver like Broadcom.  RaLink focuses on USB-based chipsets as far as I know.

Realtek as far as I know only makes USB chipsets.  They may have pretty good open-source Linux support, but I would have to do more research.  They certainly have pretty good Linux support for their audio and wired ethernet products.

That said, I would avoid these latter two manufacturers since USB-based devices will crowd out your USB bus unnecessarily.  There may also be power management benefits due to less overhead, although this would be hard to prove.  That said, PCI-E is "closer to metal" as in closer to the CPU, so I wouldn't mess with USB WIFI cards unless you need to.  I definitely like Atheros' offerings on this front, even if they just bought somebody else's chipset and improved on it.

---

### Post by walt.smith1960 on 2011-03-30
Strictly unscientific but Broadcom and Ralink seem to show up most frequently in the networking & wireless forum so personally I'll steer clear of them if I can.  I hardly ever see a problem with an Intel adapter.  I have a USB Atheros and a USB Realtek.  Both required a little tweaking but nowhere near full geek mode.  One thing to keep in mind with a PCI card is line of sight from the adapter antenna to the router.  If I had gone with a PCI card in my desktop I'd have had to get one with an antenna on a cable.  Otherwise the metal PC case would have been squarely between the adapter antennas and the router.

---

### Post by nightalon on 2011-04-03
Addendum on the AR9380:


I got the card today, Apple-branded and a beaut'.

It works pretty epically in Windows, even using WWAN antennae.  Best card I've used so far, except that I haven't tested Intel's offerings.

Also, under Ubuntu ath9k does support AR9380, but you need to get backports from at least the 2.4.36 kernel, which I did not bother to do.  Thus I didn't test the card under Ubuntu since I'm lazy.

10.04 used 2.4.32; 10.10 used 2.4.35; 11.04 will use 2.4.38.


As for MacOS, neither an up-to-date 10.6.7 system recognized the card nor did an out-of-date 10.6.4 system.  Very strange...I guess Mac Pros must have a special driver that is simply not part of the system-wide updates.  This does make some sense since there are some pretty big architectural differences between this the 9003 series and the previous 9002 series.


I also just learned that there is an AR9382 with the same feature set as the AR9280, so I'll probably replace my poorly performing AR9280 with that if it's cheap.


Also, I'll try to test the Intel options, assuming they're cheap on eBay.

---


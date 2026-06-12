---
title: "Recommendation: Low-energy,small (mini-itx?) &amp; quiet (fanless?) system with SATA RAID"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by hbf on 2007-07-16
Hi all,

I'm planning to set up my first small server at home running Ubuntu. I've previously used mostly Macintoshs, so I'm not very up-to-date on the status of the current hardware situation, especially when it comes to Linux support. So I am asking for some suggestions for hardware to get for the following requirements:

[LIST=1]
[*]Decent Linux (Ubuntu) support (obviously...).

[*] I want to run the machine as a small server (up to five clients, probably not more than two simultaneously) **mostly for backups** -- and possibly for some media storage or streaming (music).

[*] I basically will want simple ssh/rsync/... access for backups (haven't decided on backup method yet).

[*] **Hardware RAID support with some sort of mirroring** (e.g. RAID 1) is crucial for my backups (ideally on mainboard, but an extension card is also possible).

[*] Thus: At least two harddrives, ideally up to four. Ideally SATA drives. (I don't have any drives yet, so I don't want to buy the older parallel ATA harddrives. An IDE connector for a CD drive could be useful, however.)

[*] The machine should be **quiet** (absolutely required), have **low energy consumption** (required), and be **small** (I've read about **mini-ITX boards**, these seem pretty interesting; I don't really want the smallest case possible, but the system needs to be smaller than a normal desktop system). I probably want to put it into a corner in my room, without a monitor attached to it. So it needs to be as quiet as possible. I know there are **completely fanless** boards, so I am interested in this. [SIZE="1"](I also know that putting two or four harddrives in it will add a considerable amount of noise. However, I expect the machine to use power management and only spin the HDDs when necessary (not in idle mode). Also I plan to put the machine to sleep/standby when not in use and wake it remotely using wake on LAN automatically as part of my backup routines. So an **energy consumption < 5 Watt in standby mode** is a must (I've read that some boards need 15 Watt even in standby!).)[/SIZE]

[*] As mentioned, I'd like a system with passive cooling, but I am not totally sure if I can do that with two harddrives in the case as well. I guess it depends on the case as well.

[*] I don't really need the fastest **processor** or best **graphics** card available, although I think they should be **reasonably modern** because I will probably get tempted to use the machine for some media streaming as well since it's  going to be sitting there with large storage capacity anyway... :-) In terms of power consumption, I've read that the **Intel Core 2 Duo processors** are quite good and very fast, and I know there are some mini-ITX boards with support for those. Can you use these with only **passive cooling**?

[*] **Money/price**: I don't have money in abundance, of course, but I am willing to pay a little more to get a decent, hassle-free system that will last a few years. Cheap systems are nice, but it **doesn't have to be absolutely low-cost**. But I certainly don't want the top edge and most expensive stuff.
[/LIST]

So: Do you have any recommendations for hardware to get for this purpose? What mainboard? What processor? What case? (I assume the case also makes a large difference regarding the noise.) Are there particularly quiet harddrives? From what I've read, I'd go for Seagate drives.

Thank you very much for your help, I very much appreciate it! **Any tips, even short ones, are welcome.** If you need to know anything else, please post.

---

### Post by Tazix on 2007-07-16
I'm sort of looking at doing the same thing... low power home server.

So Far... I'm thinking this ITX motherboard:

[http://www.protech-ipc.com/ipc/product.asp?pid=308](http://www.protech-ipc.com/ipc/product.asp?pid=308)

Intel 945GM chipset (Should be good for Linux), takes Core 2 laptop processors, 4 sata ports (RAID 0,1,5,10 support)

The only thing I'm unsure of is a proper power supply for that board, since it's a 10-Pin instead of 20-Pin.

Also looking at getting one of these:

[http://www.enhance-tech.com/products/multidrive/q14.html](http://www.enhance-tech.com/products/multidrive/q14.html)

It puts 4 laptop drives into one 5.25 bay, and actually runs faster than a single 3.5 drive when run in RAID.  The plan is to get four 160 GB or 300GB (when the price comes down) laptop drives. (The SATA model is the Q14SA (Not the Q14SS), and difficult to find)

The other thing I'm planning on is a 19" 1U Rackmount case that is only 8.75" deep. (Takes ITX boards)... the only problem is I haven't found one (that has such a short depth) with a full 5.25 bay opening... so I'll probably have to modify one for the Q14.

Another ITX motherboard that is soon to release is the Albatron KI690.

[http://www.tweaktown.com/reviews/1132/albatron_mini_itx_ki690_am2_reviewed/index.html](http://www.tweaktown.com/reviews/1132/albatron_mini_itx_ki690_am2_reviewed/index.html)

While that's pretty cool that it can take high end desktop processors like the AMD 6000+ AM2... and has an ATi  X1250 integrated... that's not exactly low power consumption... and ATi Linux drivers aren't that great. The video is also overkill for a server (Well, most server services).

Anyway... I'm just in the preliminary stages of researching what to buy... thought I'd share what I found so far. :)

-Taz

---

### Post by hbf on 2007-07-17
Cool, thanks for your thoughts, I've gained a good bit of information from them!

The Protech board looks pretty nice. Through some browsing I've come upon this board also:

[http://de.kontron.com/index.php?id=226&cat=61&productid=1336](http://de.kontron.com/index.php?id=226&cat=61&productid=1336)

But it appears to be a bit pricey and hard to get (couldnt' find it on ebay). What's the price for the protech board by the way, I didn't see that on the info sheet. The Kontron board has even more ports, like 3 * Gigabit LAN (!), 2 * Firewire, 8 * USB.

What I'm wondering, though, is: Do you think one could use either of those boards just with passive cooling? Which processor would you recommend then?

I don't intend to use HDMI (evil!), but just out of curiosity: You'd need an additional graphics card with a HDMI port if you really needed HDMI, right? Actually, forget that, I really don't need it.

The Q14 looks pretty interesting. I'm not sure how quiet it will be, however. I read it (obviously) has a fan. Will that run just on demand? I know that the right control for fans make a lot of difference.

For me personally, I'd be willing to sacrifice some of the small size (i.e. make the machine a little bigger) if I can make it more quiet. Any idea if those small 2.5" laptop drives run more quietly than the bigger 3.5" drives. Are they less reliably/live shorter?

Do you think a larger case could get rid of a possibly noisy fan for the HDDs?

Anyway, thanks for your thoughts, and keep us updated if you find out anything new. I'll do the same! I appreciate your help.

-hbf

---

### Post by hbf on 2007-07-17
> **hbf said:**
> Through some browsing I've come upon this board also:

[http://de.kontron.com/index.php?id=226&cat=61&productid=1336](http://de.kontron.com/index.php?id=226&cat=61&productid=1336)


The link for Northern America instead of Germany is [http://us.kontron.com/index.php?id=226&cat=528&productid=1336](http://us.kontron.com/index.php?id=226&cat=528&productid=1336)

---

### Post by Tazix on 2007-07-17
Interesting board you found.  I bookmarked it for future reference.

As for the price of the Protech board, I don't know.  I didn't contact their sales dept.  That said... just about any ITX board that supports an Intel P4, Intel Mobile, or AMD Desktop processor... and has a ton of ports is going to be spendy.

You might save a few bux going back a chipset or so with a Pentium M... but you won't get a lot of ports... especially sata ports.

If room is not an issue... maybe bumping up to a Micro ATX board will do better.  There's a few 1U cases out there that are like 14"-17" deep that take those.

As for passive cooling... the only CPU's that will go fanless are either the VIA processors, or low clocked (500 MHz) Celeron type processors.... gutless wonders, IMO.  Fans are usually only noisy if the spin at a high speed.  A laptop CPU fan shouldn't be that noisy.  As for the Q14 fan... well...  it does spin at a high speed, but I couldn't tell you how noisy it is without having one first. ;)

The drives themselves should be more quiet than a standard 3.5" hard drive.  But that also depends on the drive manufacturer... I've heard some pretty "clunky" laptop drives before.  You don't really hear them spin... but the "clunky ones", you definitely hear the drive head going all over the place.

As for a larger case... there are tons out there.  Some that look like a stereo appliance... 2"-3" high, rounded corners, 14+" depth.  Those appliance type cases are usually surrounded by plastic, which insulates noise some.

Something like this: [http://www.directron.com/2699r.html](http://www.directron.com/2699r.html)

Again, that doesn't have a 5.25" bay for the Q14... but you get the idea. :)

-Taz

---

### Post by hbf on 2007-07-18
Thanks for your update.

Just for your info: I've found one dealer for the Kontron board: 349 EUR which is 482 USD. So, yes, not particularly cheap (you might get better prices in the US directly, you currently have to spend a lot of USD per EUR). So this could be a reference just to get an idea.

By the way, the 886LCD-M/mITX(BGA) board with "Intel® Mobile Celeron® 800MHz 0KB L2 Cache(mBGA479) on board" is only 50 EUR more...

Actually, the solution with two or four 2,5" drives in the Q14 sounds more and more appealing to me. I'll try to find a case for that which is not too big.

---

### Post by VorDesigns on 2007-07-18
First, is seems to me that you are taking a short view approach, up front costs versus long term savings in energy costs for power and cooling.
Thinking green for technology doesn't mean trolling eBay for a deal, it means looking for the best performing, energy efficient hardware suited to the task at hand.  Weighing the peformance goals against the long term energy costs savings and product durability.
Miniaturization of computer hardware means essentially laptop technology.  Gallantry went that way with their latest GW500 line.  The down side to this is the lack of redundancy in the drive department in that particular product line but, you still got a CLI to work with if you want it.
What you have initially described looks more like a NAS solution and you can get several consumer grade off the shelf products with a relatively modest cash outlay and very little need for user intervention beyond the use of a web browser.  Producs from Infrant (Netgear), LaCie, Buffalo Technology and many others with energy efficient, small foot print and rack mountable solutions.  These wil probably give you the most bang for the buck with the added advantage of not having to spend so much time maintaining the underpinnings.
Don't get me wrong, if you want to build a solution from scratch, more power to you.

---

### Post by hbf on 2007-07-19
> **VorDesigns said:**
> 
What you have initially described looks more like a NAS solution and you can get several consumer grade off the shelf products with a relatively modest cash outlay and very little need for user intervention beyond the use of a web browser.  Producs from Infrant (Netgear), LaCie, Buffalo Technology and many others with energy efficient, small foot print and rack mountable solutions.  These wil probably give you the most bang for the buck with the added advantage of not having to spend so much time maintaining the underpinnings.

Actually my starting point for this **was** to get an Infrant ReadyNAS. Like you said, I liked the idea of a small, ready-built system. Here's why I decided to also look for alternatives to build my own system:
[LIST]
[*]The Infrant ReadyNAS does not support wake on LAN, meaning the system would be running all the time with something like 50 W in idle mode (forgot the exact figure, but it was something like this) or it'd be off usually and I'd need to go into the basement or a different room each time I want to make a backup (doesn't fit my idea of an automated process). This was actually the main reason against the ReadyNAS.
[*]The ReadyNAS systems appeared very expensive to me. Starting at 950 EUR with four 250 GB drives. So basically I thought, "why not build my own system for less or the same price and get a system I can run any system/application on, not only CLI based backups, if I want to."
[/LIST]
As for other NAS solutions: The other ones focused onto the consumer market mostly seemed to be for only one HDD, but I would like to use two or four drives in RAID.

> **VorDesigns said:**
> First, is seems to me that you are taking a short view approach, up front costs versus long term savings in energy costs for power and cooling.
Thinking green for technology doesn't mean trolling eBay for a deal, it means looking for the best performing, energy efficient hardware suited to the task at hand.  Weighing the performance goals against the long term energy costs savings and product durability.

I'm not really thinking to save money by buying a really expensive but energy-efficient system through the lower costs for power over time. The main reason I am interested in passive cooling and thus, as a requirement for that, low-energy systems is that I want a **quiet** system. I am a bit 'traumatised', so to speak, by my external HDD I currently use for backups (its noise I driving me nuts) and the switch I once bought a long time ago for our home network in the basement (when I installed it, I learned that it has a fan so loud as a motorway, for a component I thought wouldn't need any active cooling at all). Plus I just don't like the idea of using 50 W for a box in the corner doing nothing most of the time.

That being said, I haven't ruled out the possibility to build my own *low-cost* system, e.g. with a Celeron 800. Like getting one of those media stations a large telecom company is giving its customers for TV over the internet on eBay, take it apart, put in a RAID controller and use a different case.

> **VorDesigns said:**
> 
Don't get me wrong, if you want to build a solution from scratch, more power to you.

Yes, initially I wanted only a NAS system, but I was tempted to get more power, options and control for a comparable price. I currently only have a Macintosh PPC laptop, so I was thinking the box I am planning here could also serve as a 'desktop' computer or music repository/streamer. Plus I'm always curious about what's possible. I understand my goals could well be misunderstood through my descriptions here.

> **VorDesigns said:**
> Miniaturization of computer hardware means essentially laptop technology.  Gallantry went that way with their latest GW500 line.  The down side to this is the lack of redundancy in the drive department in that particular product line but, you still got a CLI to work with if you want it.

Thanks for this info, I'll look into it!

---

### Post by Tazix on 2007-07-20
> **VorDesigns said:**
> First, is seems to me that you are taking a short view approach, up front costs versus long term savings in energy costs for power and cooling.
Thinking green for technology doesn't mean trolling eBay for a deal, it means looking for the best performing, energy efficient hardware suited to the task at hand.  Weighing the peformance goals against the long term energy costs savings and product durability.

Not sure if that was directed at me or not... But I have no issues with the hardware costs.  Some of it I will wait for price drops though.... because I know the price will drop.

> **VorDesigns said:**
> What you have initially described looks more like a NAS solution and you can get several consumer grade off the shelf products with a relatively modest cash outlay and very little need for user intervention beyond the use of a web browser. 

If all I wanted was a NAS, I'd buy one.  My project is going to be a complete server...  some permanent services (CIFS,FTP, WEB, etc.), some will  betemporary / experimental ( for example... directory services: Fedora DS, OpenLDAP, OpenDS, Apache Directory, etc.) 

I can do all that stuff on my present machine running Linux... however I  wish to have more room and run it 24 / 7.

-Taz

---

### Post by hbf on 2007-08-24
Just a quick info for anyone who is interested in the [Quadrapack Q14]("http://www.enhance-tech.com/products/multidrive/q14.html") from Enhance Tech. When contacting Enhance Tech for a supplier in Europe and specifically asking for the Q14SA (SATA) as opposed to the Q14SS (SAS) version, I received the following answer:

> 
From: XXX [mailto:XXX] 
Sent: Thursday, August 23, 2007 9:00 PM
To: XXX
Subject: Q14SS: Information Request
 
The Q14SS has permanently replaced the Q14SA and supports both SATA and SAS.


Just so you know. That also explains why the Q14SA is hard to obtain, as you wrote.  Indeed the Q14SS is also very hard to get, and pretty expensive. I think I saw it on one of the distributor sites listed on Enhance Tech's website for about 140 USD. In Europe I basically couldn't find any supplier, until I received this from a company in Germany (found by Enhance Tech):

> 
Dear Sir,
 
Thank you for your interest on the Q14SS.
End user unit price is 174 Euros.
We have them on stock, so please let us know your Billing & Shipping address, so that we can issue an invoice.
 
Best regards,
Peter
 
--
Peter J. Lee
Director, International Business Development
CO-WORLD GmbH
Auf der Kaiserfuhr 39
53127 Bonn, Germany
 
Tel  XXX
Fax. XXX
Mobile XXX
E-Mail XXX
Web [http://www.coworldcs.com](http://www.coworldcs.com) 


I think I'll abstain from getting one for that price... :-(

---

### Post by hbf on 2007-08-24
> **Tazix said:**
> 
The other thing I'm planning on is a 19" 1U Rackmount case that is only 8.75" deep. (Takes ITX boards)... the only problem is I haven't found one (that has such a short depth) with a full 5.25 bay opening... so I'll probably have to modify one for the Q14.


Before I forget, a case I've been considering is the [LC 05]("http://www.silverstonetek.com/products/p_contents.php?pno=lc05&area=") from Silverstone. I was originally interested in it because it has a 5.25" bay (to be used for the Q14) which is really rare for cases of that size.

As I mentioned I probably won't get the Q14 because of the price, but it is still a very interesting one because it can hold four drives 2.5" internally (without using the Q14), as I was told by someone from a computer store specialised in such systems.

The only problem preventing me from getting my ideal configuration now is that one can't put a Kontron 986 board in it with an Intel Core 2 Duo CPU -- no room for the fan and heatpipes don't quite work with the case. (As metioned, I've moved away a bit from a pure storage NAS type server as described in my initial post to a multifunctional device with decent computing power -- I might as well use it for other things if I have a box standing around!).

And obviously the LC05 it is not a 19'" rackmount case, I don't know how important that is to you.

All in all, for everyone interested in the same topic, I can assure you it is quite hard to find compoents for a small system if you have special requirements such as several hard drives or low noise emission / passive cooling!

---


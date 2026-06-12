---
title: "Basic Printer Wanted"
date: 2012-08-01
forum: Hardware
---

### Post by Ubun2to on 2012-08-01
My printer just broke down, and I decided that it was time to trash it. I dropped it off at a recycling center, and now I'm trying to find a basic color printer (I already have a scanner, so I don't need an all in one combo, plus I would never have any use for a fax machine).
I just need a printer that does color prints and copies that works with Ubuntu 12.04. I've checked all over, and I can't find any recent printers (as in ones produced during or after 2010) that I can confirm will work with 12.04. I want to stay under $150, and I don't want ridiculously expensive ink (although there is a CartridgeWorld store near my house, so I am not too worried about expensive ink-they refill the cartridges for about 75% cheaper than buying new cartridges in my experience).
TL;DR-I need a color printer/copier that works with 12.04 and is fairly recent (as in up to 2 years old) for under $150.
Any suggestions?
Also, having open source drivers available would be nice, as they would be more likely to be maintained in future versions of Ubuntu.

---

### Post by kurt18947 on 2012-08-01
Where are you?  If you're in the U.S. and have a Staples nearby, you could see if this is available:

[http://weeklyad.staples.com/Staples/BrowseByPage?storeid=2278774&promotionviewmode=2&promotioncode=Staples-120729&listingid=0&sneakpeek=N](http://weeklyad.staples.com/Staples/BrowseByPage?storeid=2278774&promotionviewmode=2&promotioncode=Staples-120729&listingid=0&sneakpeek=N)

Brother MFC-J430W for $49.99 is hard to beat.  SWMBO has one, paid $69.99 and was still not much more money than new ink cartridges for her old HP printer and yes, it works well with Ubuntu.  It had issues with 12.04 when 12.04 was in beta/just released but the problem has been fixed.   I know you don't need scan and fax but for $49.99 why not?

---

### Post by na5h on 2012-08-01
As far as I know, HP printers tend to work well with Ubuntu...and they start at a cheap price.

---

### Post by gifford on 2012-08-01
My experience with Brother devices and Linux has been great. Competitive pricing and good quality. Some drivers are in synaptic and others on their website.

---

### Post by na5h on 2012-08-02
Just thought I'd add that the HP printers that I've been dealing with in Ubuntu didn't require any manual installation of drivers...they worked out of the box...

---

### Post by Ubun2to on 2012-08-02
> **kurt18947 said:**
> Where are you?  If you're in the U.S. and have a Staples nearby, you could see if this is available:

[http://weeklyad.staples.com/Staples/BrowseByPage?storeid=2278774&promotionviewmode=2&promotioncode=Staples-120729&listingid=0&sneakpeek=N](http://weeklyad.staples.com/Staples/BrowseByPage?storeid=2278774&promotionviewmode=2&promotioncode=Staples-120729&listingid=0&sneakpeek=N)

Brother MFC-J430W for $49.99 is hard to beat.  SWMBO has one, paid $69.99 and was still not much more money than new ink cartridges for her old HP printer and yes, it works well with Ubuntu.  It had issues with 12.04 when 12.04 was in beta/just released but the problem has been fixed.   I know you don't need scan and fax but for $49.99 why not?

I am in the USA. I bought the printer, and I think it's a great price considering it's an all in one. Looks like I can ditch my scanner. I don't need a fax machine, but why bother opting out of it-there's no use trying to find one without it.

---

### Post by kurt18947 on 2012-08-03
> **Ubun2to said:**
> I am in the USA. I bought the printer, and I think it's a great price considering it's an all in one. Looks like I can ditch my scanner. I don't need a fax machine, but why bother opting out of it-there's no use trying to find one without it.

You may never use the fax function but having an alphanumeric keypad is can certainly be useful for setting up wireless networks.

---

### Post by Ubun2to on 2012-08-03
> **kurt18947 said:**
> You may never use the fax function but having an alphanumeric keypad is can certainly be useful for setting up wireless networks.

I never even realized this thing had WiFi on it. This is nice-I no longer have to keep my computer on if I want to print from another.

---

### Post by kurt18947 on 2012-08-03
> **Ubun2to said:**
> I never even realized this thing had WiFi on it. This is nice-I no longer have to keep my computer on if I want to print from another.

Oh yeah,  one of the benefits of networkable printers.  It also supports wireless N speeds so I don't see much difference in responsiveness between wireless networking and the USB connection.  You can also have both connections active.     Kinda handy to have a USB connection to a main P.C.  and still be able to print and scan wirelessly from other devices.

---

### Post by Ubun2to on 2012-08-03
> **kurt18947 said:**
> Oh yeah,  one of the benefits of networkable printers.  It also supports wireless N speeds so I don't see much difference in responsiveness between wireless networking and the USB connection.  You can also have both connections active.     Kinda handy to have a USB connection to a main P.C.  and still be able to print and scan wirelessly from other devices.

I already recieved mine. I set it up, and it works GREAT!
I had to play around with the CUPS config file, and had to switch it to AppSocket (socket://192.168.1.9), but I think it was worth it.

---

### Post by kurt18947 on 2012-08-04
> **Ubun2to said:**
> I already recieved mine. I set it up, and it works GREAT!
I had to play around with the CUPS config file, and had to switch it to AppSocket (socket://192.168.1.9), but I think it was worth it.

Good job.  I've found AppSocket to be very reliable.  I'd tried other connections and it'd seem to install correctly but then I'd try to print over the network a week later and get a "printer not found" type message.  Using Appsocket I prefer the machine have a static I.P. which is one place the alphanumeric keypad on the machine is handy.

---

### Post by Ubun2to on 2012-08-04
> **kurt18947 said:**
> Good job.  I've found AppSocket to be very reliable.  I'd tried other connections and it'd seem to install correctly but then I'd try to print over the network a week later and get a "printer not found" type message.  Using Appsocket I prefer the machine have a static I.P. which is one place the alphanumeric keypad on the machine is handy.

Gotta love static IPs. Things I like about the printer:
1. Cheap.
2. Easy loading process for ink.
3. Wireless (I didn't even connect it to a computer for setup!)
4. Keypad (easy WiFi setup-I have a long password).
5. Scanning=easy (didn't take very long to setup, and it works with the built in scanning software).
6. 8 Bit soundtrack on startup (yes, I know what 8 bit music sound like-I've played on an SNES several times).
7. Works as claimed (seems uncommon in these times).
8. Fairly quick to print in color and black and white.
9. Actually works with Linux.
10. 2 trays for paper.
11. Scanner is fairly decent.
12. Print quality is good (I don't have high expectations, or big requirements for a printer).
Things I dislike:
1. Driver takes some work to get (not the worst, but I dislike having to manually select AppSocket from CUPS web interface).
2. Weird noise after print job is done (probably just the cartridges resetting, but still annoying).
3. Loading paper in bottom tray can be annoying (if there is already paper in it, it will not slide forth with the tray, and I have to do it manually).
4. Easy paper jam clearing (haven't had to do this yet, but I have noticed how to clear the jams, and it looks pretty easy-I hate how some printers have to be taken apart just to clear 1 jam).
My favorite thing about it has to be the 8 bit soundtrack when it starts-when I was young, I had a friend who never upgraded from his old SNES. It brings back memories.

---


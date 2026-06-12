---
title: "Which Ubuntu friendly netbook for wife?"
date: 2010-03-18
forum: Hardware
---

### Post by Johny79 on 2010-03-18
Ok so my wife wants a netbook for various reasons, one being to play Facebook games on her breaks (she works nights), so I've got the following list of needs and 'nice to haves'(this is her list not mine btw, lol)...

Needs:

No smaller than a 10" screen.
Wireless b/g
To work with Ubuntu 9.10 netbook remix without too much hassle getting things working
Be able to run Facebook games pretty well (Cafe World, Farmville, Island Paradise)

Nice to have:

Bluetooth (I'll just buy a mini dongle if it's not built in)
Wireless n
Webcam
Be pink (typical woman!)

At the moment I'm thinking the [MSI Wind U130 (clicky)]("http://www.msi.com/index.php?func=proddesc&maincat_no=135&prod_no=1969") with the following spec...    

* Intel Atom N450 1.66GHz processor.
* 1GB DDR2 RAM.
* 10in screen (1024 x 600 pixels).
* 160GB SATA hard drive.
* Intel NM10 graphics.
* Multi card reader.
* 3 USB ports.
* Bluetooth.
* 1.3MP webcam.
* 802.11 b/g/n wireless enabled.

Mainly because I can pick one up for £190 in a local store, which seems a good bargain, especially as it's available in black, white, or... pink! lol

Anyone out there running on this system? Or something similar? Or have an entirely different recommendation?

Any help or advice would be appreciated! :)

---

### Post by blakep2 on 2010-03-18
what exactly are you looking for?

---

### Post by tuddy666 on 2010-03-18
Have a look at this page- [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")

Any of the machines in Tier 1 should work well with UNR. There doesn't seem to be a compatibility report for the Wind U130, sadly. 

Personally, I use an Acer Aspire D250 (one of the models made before they started to use the GMA 500) and it works great. All I had to do was install the proprietary drivers for the Broadcom chipset through the "restricted drivers" menu.

---

### Post by wojox on 2010-03-18
Check into Dell Studio. You can even get it in pink I believe.

---

### Post by blur xc on 2010-03-18
Facebook games might be spotty on a netbook.  Some work better than others though.  I'd personally shy away from the gma 500, unless there have been new developments I'm not aware of.  My wife has a Dell mini 10 w/ Ubuntu 9.10 nbr on it, and it's definitely not a match made in heaven.  It has frequent crashes, hangup, video and display problems, sound quit, etc...

For 99% of things, Flash works fantastic on my Desktop PC, and one of my favorite time wasters is TG Motocross 3 on [www.teagames.com](www.teagames.com).  The recently put that game on Facebook, so I hopped on my wife's account and tried playing it- but it was slow and choppy- completely un-playable...  

For the record- Flash on a netbook isn't fantastic in Windows either.  

BM

---

### Post by norseman-has-a-laptop on 2010-03-18
wel does your wife know how to use a computer?

---

### Post by jrssystemsnet on 2010-03-18
Be warned that while the Broadcom BCM43xx wireless NICs are *supported* in Ubuntu, they are still unmitigated pieces of crap and will give you no end of trouble.  So either be wary of buying anything with one of these wireless cards in it, or be prepared to pick up an Intel wireless card to replace it with.

This is not an Ubuntu problem, the BCM43xx cards suck under any OS, Windows included.

I did have good results with a netbook that had an Atheros chipset wireless NIC in it, but I've never tried to buy an Atheros wNIC to use as a replacement, so I can't tell you for certain what model to look for if you go that route.  But in general, on a netbook (since they're a pretty recent platform), Atheros wireless will probably be a win, Broadcom wireless will almost certainly be complete fail, and Intel will rock but as of right now I don't know of any stock netbook configuration that includes the Intel card.

Also FYI, netbooks generally take a **half-height** mini-PCIe card, not the standard full-height mini-PCIe that most standard laptops take - so if you are going to go the replacement route, be sure of the form factor you need before you order anything.

---

### Post by jrssystemsnet on 2010-03-18
Looks like that MSI Wind you linked will be using the Atheros wireless, so that ought to be good.  Just make sure that you can stand the keyboard and touchpad on it - form factor is a MAJOR usability concern for netbooks, which is why I personally use Dell Mini 10v netbooks despite them coming with the crap BCM4311 wireless. :)

---

### Post by norseman-has-a-laptop on 2010-03-18
> **jrssystemsnet said:**
> Be warned that while the Broadcom BCM43xx wireless NICs are *supported* in Ubuntu, they are still unmitigated pieces of crap and will give you no end of trouble.  So either be wary of buying anything with one of these wireless cards in it, or be prepared to pick up an Intel wireless card to replace it with.

This is not an Ubuntu problem, the BCM43xx cards suck under any OS, Windows included.

I did have good results with a netbook that had an Atheros chipset wireless NIC in it, but I've never tried to buy an Atheros wNIC to use as a replacement, so I can't tell you for certain what model to look for if you go that route.  But in general, on a netbook (since they're a pretty recent platform), Atheros wireless will probably be a win, Broadcom wireless will almost certainly be complete fail, and Intel will rock but as of right now I don't know of any stock netbook configuration that includes the Intel card.

Also FYI, netbooks generally take a **half-height** mini-PCIe card, not the standard full-height mini-PCIe that most standard laptops take - so if you are going to go the replacement route, be sure of the form factor you need before you order anything. i havent had any problems with my broadcom BCM43xx yet lol i guess i should wait then

---

### Post by jrssystemsnet on 2010-03-18
> **norseman-has-a-laptop said:**
> i havent had any problems with my broadcom BCM43xx yet lol i guess i should wait thenIf you have relatively high signal strength from your own wireless AND low contention (ie not a lot of other wireless networks in the area), they work OK for basic web browsing.  But if you have a bigger house, or an upstairs/downstairs environment, or a lot of contention (neighbors who have wireless of their own, or multiple users on your own wireless network), you end up with a lot of network "freezing" and/or outright drops.  

Also, even under ideal conditions, it takes a LOT longer for the BCM43xx cards to connect to a wLAN than it does for the Atheros or Intel cards (like 45 seconds as opposed to about 10 seconds), which can be mind-numbingly frustrating if you let your netbook go into suspend mode frequently.

---


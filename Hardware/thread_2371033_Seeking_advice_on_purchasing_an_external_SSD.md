---
title: "Seeking advice on purchasing an external SSD"
date: 2017-09-09
forum: Hardware
---

### Post by satimis on 2017-09-09
Hi,

This is my first time using external SSD drive.

I'm going to purchase a ADATA SD700 256GB USB3.1 Gen 1 External SSD ASD700-256GU3-CBK 

[http://www.adata.com/en/feature/441](http://www.adata.com/en/feature/441)

to be used on Raspberry Pi3 Model which only provides USD ports.  Is an external SSD only providing one USB connector which is for both power and Data connection?

Can it used on Raspberry Pi3 Model B?

Thanks in advance.

Regards
satimis

---

### Post by efflandt on 2017-09-10
If using an external drive on a Raspberry Pi you very likely need to use a powered USB hub for the drive. I don't know how much power the 3 model uses, but earlier Pi's had a 700 mA PSU that could power the Pi and a couple of low power (100 mA) USB devices, like dongles for mouse/keyboard, WiFi, memory stick, etc. Spec's for the drive you are looking at says it needs DC 5V, 900mA, so power for the powered USB hub should be at least 1 Amp if not 2 Amps.

---

### Post by satimis on 2017-09-10
> **efflandt said:**
> If using an external drive on a Raspberry Pi you very likely need to use a powered USB hub for the drive. I don't know how much power the 3 model uses, but earlier Pi's had a 700 mA PSU that could power the Pi and a couple of low power (100 mA) USB devices, like dongles for mouse/keyboard, WiFi, memory stick, etc. Spec's for the drive you are looking at says it needs DC 5V, 900mA, so power for the powered USB hub should be at least 1 Amp if not 2 Amps.

Hi,

Thanks for your advice.

I use a Samsung power supply for my mobile phone S6, output 5V 2A, to run Raspberry Pi3 B.  It works without problem.

This is only a test on Raspberry without practical use.  I have powerful desktops at home, AMD 8-core PCs with 32G/64G RAM installed.

I have old internal HDs such as 1T/1.2T WD, black label, and ADATA 120G SSD here which are installed on PCs for old data storage.

I have made some search on Internet.  To connect an internal HD to Raspberry Pi I need to convert it to external first which I need to buy a kit as shown on following video;

How to convert an internal hard drive to external (easiest way)
[https://www.youtube.com/watch?v=jp_bsAdzCrk](https://www.youtube.com/watch?v=jp_bsAdzCrk)

But to connect an External HD to Raspberry Pi I don't need the abovementioned kit as shown in following video

Raspberry Pi 2 External Hard Drive Installation: Part 3 - a Step-by-Step Guide!
[https://www.youtube.com/watch?v=NRaesLtPY4A](https://www.youtube.com/watch?v=NRaesLtPY4A)

Rather than to buy the kit for one time use I'm willing to pay more to buy an external SSD HD which I can use in my internal network later for storage.  That is the complete story.

Suggestion would be appreciated.  Thanks

Regards
satimis

---

### Post by Bucky Ball on 2017-09-10
I'll go one further; if you are using an external drive on a Raspberry Pi it MUST have its own power. Do NOT power it from the USB on the RPi. That is not good and the dinky little thing won't like.

You either need a POWERED USB hub (a USB hub with its OWN external power supply) plugged in to the Pi then the drive plugged into the hub or the drive itself needs its own power supply.

Repeat, do not use an external drive that has not got its own external power source. Do not expect the RPi to power an external drive (or anything beyond a thumb drive, really). 

Good luck.

PS: A dock is probably a much better option. I have a USB3 double-dock which I can put two drives in, SSD or HDD. You may want to add another drive or use another drive later on and a hassle with one external case. That means you need to buy another external case or swap them out. With a drive dock, simply pull one drive and plop in the other, done. Or use both at once with a dual-dock. ;)

[Something like this]("https://www.ebay.com.au/sch/items/?_nkw=dual+hard+drive+docking+station&_sacat=&_ex_kw=&_mPrRngCbx=1&_udlo=&_udhi=&_sop=12&rmvSB=true") is what I'm talking about. Used to have a bunch of external drives in their own cases, now I have a bunch of drives and one dual-dock.

Avoid thinking of the Pi as a regular computer. It's not. It's a dinky educational/development device that happens to be capable of running some neat software. It has a 5watt external PSU which is just enough to power itself, nothing else. Not a tower, not designed to power a bunch of external stuff hanging off it. That all needs to run under its own steam.

Hope that helps in some way.

---

### Post by gordintoronto on 2017-09-10
I don't see the point of an external SSD on a Pi. Even a slow hard drive will be much faster than the USB port on the Pi.

---


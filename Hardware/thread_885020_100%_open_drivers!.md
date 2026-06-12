---
title: "100% open drivers!"
date: 2008-08-09
forum: Hardware
---

### Post by cult hero on 2008-08-09
I've been very, very impressed with Ubuntu in the 8.04 release and while I left the Linux world for a Mac a few years ago, I like both quite a lot and idealistically I like Linux better. 

I'm seriously considering building my next machine purely for Linux. So, my questions are these:

1. I know Intel produces open source drivers, so I'm leaning in the direction of an Intel board with built in video. It's not greased lightning, but it'll due. However, I remember reading something about ATi opening up more with the help of Novell. However, when trying to see the current status, all I can find via google are press releases that are about a year old. Anyone know what's up with that?

2. Sound. Although it's easy to find compatible sound cards, is there any company that's released open sound drivers? (What about the built on sound from Intel?) Furthermore, is there anyone out there that's used this stuff?

3. Any other general suggestions on fully supported hardware?

I've gotten used to the "just works" Mac deal (which doesn't always, but is generally very good) and frankly, Ubuntu has been excellent EXCEPT where I've run into hardware troubles. So I figure if I build a machine to spec I might get the same deal.

---

### Post by AusIV4 on 2008-08-09
I have Intel graphics, wireless, and sound. All work out of the box with Ubuntu.

---

### Post by ThaRabbit on 2008-08-09
from what I know, ati drivers are getting there but still not up to par.

nVidia drivers seem to be dodgy with the latest cards too, though the latest drivers are doing better. Older cards (6xxx range) are fine, "go" models are dodgy.

I use intel here, onboard x3100, works out of the box and has more than enough punch to smoothly run compiz effects :)

---

### Post by Yellow Pasque on 2008-08-09
The issue with open drivers seems to be more of a problem with X.org/mesa/DRI in general. nVidia has long-since rewritten major portions for OpenGL support and memory-managment in their binary driver. Intel is moving in that direction with GEM, and ATI is trying to fix the issues (DRI2). It's a bit of a mess at the moment.

**For open-source drivers**:

ATI: your best bet at the moment is an X1K(R500) card or a 690G board and using the AtomBIOS or "quick-and-dirty-2D" branch of the radeonhd driver. I can't recommend the ati/radeon driver for anything newer than Radeon 9800, as I've always experienced hang-ups and other bugs with it. The radeonhd guys are working on R600/R700 (they're very similar architecturally) at the moment. IMHO, they're not the fastest driver-writing team, but they do things right, even if it means waiting on documentation.

Intel: Their onboard video isn't for hard-core gaming or graphics designers, but they look to be moving in the right direction for a good 2D/Compiz/Xv solution: [http://www.phoronix.com/scan.php?page=news_item&px=NjY0Nw](http://www.phoronix.com/scan.php?page=news_item&px=NjY0Nw) Larrabee is coming too...

Nvidia: Check out Nouveau, reverse-engineered open-source drivers (probably not the best solution)

Use phoronix.com to keep abreast of the developments.

**Sound** - ALSA is open-source, as is OSS4 (except for Lynx Studio drivers). Avoid the Creative X-fi cards and chipsets. The best solution at the moment looks to be an envy24ht-based card with OSS4 (ESI Juli@, M-Audio Revolution) or a C-Media CMI-8788 card (bgears b-Enspirer). Auzentech used to make some nice CMI-8788 cards, but Asus recently struck a deal with C-Media for exclusive rights to the chip for their Xonar line, which isn't fully-supported (digital out, surround) at the moment.

---

### Post by BlueSkyNIS on 2008-08-09
You guys are mentioning Intel integrated x3100 graphics...

I have a 24 inch monitor with 1680x1050 resolution. Can x3100 run full blown (extra) compiz effects or only default (normal) ones?

What's about ATI 780G graphics?

---

### Post by ThaRabbit on 2008-08-10
> **BlueSkyNIS said:**
> You guys are mentioning Intel integrated x3100 graphics...

I have a 24 inch monitor with 1680x1050 resolution. Can x3100 run full blown (extra) compiz effects or only default (normal) ones?

What's about ATI 780G graphics?

I'm running full blown compiz on 1280 x 800, though I should mention that the "fire" effects with thousands of particles is asking too much.

Wobbely windows, desktop cube, open / close animations (as long as it's not fire) are working smooth.

---

### Post by BlueSkyNIS on 2008-08-10
> **ThaRabbit said:**
> I'm running full blown compiz on 1280 x 800, though I should mention that the "fire" effects with thousands of particles is asking too much.

Wobbely windows, desktop cube, open / close animations (as long as it's not fire) are working smooth.

OK, thanks for the info :D

---

### Post by stinkinrich88 on 2008-08-10
srsly, don't get an ATI card, I've regretted it ever since. Mipmaps don't work in compiz (or blur) and right now I'm having great trouble getting 4gb ram working with ati open drivers. It's a nightmare. get a nice little nvidia card, I had no trouble at all with that.

My intel board with onboard sound works lovely! I doubt you'll get much trouble getting onboard sound on any board to work

---


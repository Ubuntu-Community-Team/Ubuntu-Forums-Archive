---
title: "When Boot from CD, after the loading, it goes white n nothing happens"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by R0CKABILLY on 2009-01-31
Hey there..

I'm Guntur from Indonesia

I want to install ubuntu 8.10 in my desktop pc..

i use windows xp..

i do boot the ubuntu 8.10 cd that i created from the iso file..

n ubuntu installation menu come out.. i click the install ubuntu.

then the loading thing comes out.. n after the loading completed, it turns into a blank white screen.. n i can't do anything..

any clue for this?

as another information, i try install linux mint n i got the same problem..

here's my computer spec :

Gigabyte GA 965 P DS4
Intel Core 2 Duo E 6600
Sapphire ATI Radeon HD 4850
Patriot 1 GB x2
Creative X-Fi Fatality
WDC 250 GB x2
WDC 1 TB x2

---

### Post by lemming465 on 2009-02-01
The 8.10 installer is using a bleeding edge version of the Xorg stuff, and there are glitches with a variety of  ATI, Nvidia, and Intel video chipsets.  You might want to try using a text-based alternate install disk.  You'd probably have to do your first login and update at a text console, but once it was patched current you could probably run *sudo dpkg-reconfigure xserver-xorg* and get to a working video configuration.

---

### Post by JSchoeck on 2009-02-04
I've got the same issue with an ATI HD 4870 card (on an AMD Phenom II system).

Is there a tutorial somewhere that describes the exact steps what to do after using the alternate install CD?

I want to seriously start using Ubuntu with this PC and I've been held up quite bad by not being able to even install it.

Greets

---

### Post by JSchoeck on 2009-02-06
The answer to my problem was simple:
[LIST]
[*]Press F4 in the "boot menu" of the install- / live-CD (where you can choose to install or try Ubuntu, or do a memtest, etc.).
[*]Choose safe graphics mode
[*]Proceed with trying or installing Ubuntu as usual
[/LIST]


I hope this helps some people. I'm enjoying a smoothly running Ibex now - and I can even hibernate without any problem! :)

Best wishes,
Johannes

---


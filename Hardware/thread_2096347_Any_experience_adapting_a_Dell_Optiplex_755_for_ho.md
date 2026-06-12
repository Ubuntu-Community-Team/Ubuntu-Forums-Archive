---
title: "Any experience adapting a Dell Optiplex 755 for home use?"
date: 2012-12-19
forum: Hardware
---

### Post by abelundercity on 2012-12-19
My workplace is having a silent auction to get rid of some of its old workstations, which would be a considerable upgrade from my home computer, which I cheerfully refer to as The Relic.  I'm fairly confident that my bid will see me taking one of the office models home.

After a few searches, I thought I'd best take my inquiry here and get the real expert opinion.

Aside from installing Ubuntu (a given), are there other things I should take into consideration in adapting this computer for home use?

3D acceleration is a must, as I'm active in Second Life and World of Warcraft.  I've read that the 755 may have clearance problems with some 3D cards.

---

### Post by bfmetcalf on 2012-12-19
I'm staring at one right now and have a hunch that it will be difficult to fit much of a card in the thing at all.  You could probably tear it apart and get a cheep larger case to put it all back in though.

---

### Post by abelundercity on 2012-12-23
I've yet to lay eyes on the thing, and the documentation is somewhat less than helpful when it comes to the case form factor. Will an ATX do?

---

### Post by jmate24 on 2012-12-23
Yes, I think so.

---

### Post by lykwydchykyn on 2012-12-24
Not entirely sure about the 755, but I used a 745 at work and have a couple of small-form-factor 745s at home for the kids.

You definitely don't want the onboard intel graphics HW, it takes some monkeying around to get 1280x1024 out of it, nevermind gaming-level graphics acceleration.

At work we used some of the low-profile graphics cards to put in Nvidia dual-monitor cards.  Worked fine, just make sure you get a low-profile card.

---

### Post by abelundercity on 2012-12-25
Would I need to be concerned if the card was PCIe 2.0?  The Relic uses AGP, so this is new ground for me.  Just want to know I've got my bases covered.

---

### Post by PhilGil on 2012-12-26
Not all 755's are small form factor models. I have a 755 sitting under my desk right now and it's in a standard mini-tower desktop case.

I'm running Debian Testing (similar packages to Ubuntu 12.04) and everything works out of the box. 3D acceleration using the integrated graphics is sufficient for Gnome 3 effects and HD video.

I don't game, but my assumption would be that an aftermarket graphics card would be (almost) a necessity. My case would accommodate any single-slot PCIe card. As other posters have mentioned, you can shoehorn a graphics card into a small form factor case, but you'll need a compact card.

Another consideration is the card's power draw. Typically you'll find that the power supply in a machine like this won't have the excess wattage to support a high-end graphics card.

I like my 755. It runs Linux well and has more than sufficient power for day to day computing.

---

### Post by abelundercity on 2012-12-26
"High end" has never really been a concern of mine, though I'd like the chance for it to be. ;)

Assuming the machine does turn out to be small form factor, this is the card I have in mind for it: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130586](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130586)

---

### Post by N00b-un-2 on 2012-12-26
I'm using a MUCH older Dell Optiplex 320 (Mid Tower, not the mATX model).  It did take a bit more tweaking than most other hard ware that I've installed Linux on in the past, but a handful of inexpensive hardware upgrades like RAM and basic nVidia card and it handles modern Linux like a champ.  It was possible to get the onboard ATI graphics working, but caused some issues with compositing enabled and the amount of RAM the system would see and use.

The Optiplex 755 should be perfect candidate for running Ubuntu on

---

### Post by abelundercity on 2013-01-15
OK, I've confirmed that it's the mini tower form factor, and that I'm pretty much a shoo-in for the auction.  Dell's specs put a 305W power supply in there.  Would that be enough to support two hard drives, an optical drive (not sure if ROM or RW yet), and an entry-level 1 GB graphics card?  Or should I start shopping for a new power supply as well?

---

### Post by lykwydchykyn on 2013-01-15
I don't think you'll need to upgrade the PSU.  I've added at least that much to optiplexes in the past, and never gave the stock PSU a second thought.

---

### Post by abelundercity on 2013-01-15
OK, great! So one last question (hopefully): Will a PCIe 2.0 card work in a 1.0 slot?

Yes, it has been a really long time since I last upgraded my hardware.

---


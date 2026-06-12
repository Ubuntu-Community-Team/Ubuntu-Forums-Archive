---
title: "PCI USB card..??"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by icehammer on 2007-01-29
My USB ports stopped working recently, so i decided to buy a Internal USB card instead of getting the mainboad repaired, as it was turning out to be much cheaper.. Now, the card(s) that i saw in the mkt all say "Windows 98/ME/2000/XP"... And neither do their CDs contain any driver for linux..

1. Is a driver required in the first place?
2. If no, how do i get linux to recognize my new card??

The shopkeeper says it'll mount itself, but i have doubts.. Linux is not very known here in India, so i don't wanna beleive my shopkeeper..


Plz reply asap..

---

### Post by allwin on 2007-01-29
With any luck the card MIGHT work.  I had a old PC with usb 1.1 ports on it and put in a usb 2.0/PCI card.  It got detected, however, I haven't been able to get anything to work at a 2.0 speed.  So it gets recognized, devices work...but super slow.  Hope you are luckier.  It's a good fix if you must have connections at any price, so to speak!

---

### Post by florizs on 2007-01-31
well do you know what the brand and model type of the card are?
if so try googling them or looking it up in the ubuntu hardware database.

---

### Post by RandomJoe on 2007-01-31
I haven't run across a USB add-in card that _didn't_ work, although I certainly expect there are some that won't.  I currently have two here.

The best one I have - naturally - cost a bit.  I purchased an Adaptec DuoConnect card that has firewire as well as USB2 ports.  It shows in 'lspci' to have an NEC USB chipset and TI firewire chipset.

I also have a card that was left in a computer someone gave me, looking it up IIRC it was an IOGear card (about $15 US) and 'lspci' says it is an ALi chipset.  It too works well.

---

### Post by icehammer on 2007-02-01
ok, works..

thanks guys..

---


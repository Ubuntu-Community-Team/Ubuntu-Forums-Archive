---
title: "problems with two video cards desktop system"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Stanley Krute on 2009-11-01
I've got a desktop system with two video cards: an nVidia GeForce 6200 and a Matrox Mystique PCI. Each card has a single monitor attached to it.

Just installed Ubuntu 9.10 from Windows XP using Wubi. Everything went well, except that only one video card and monitor -- the nVidia -- is working. The Matrox Mystique is not. I don't even think it's recognized as existing.

Anyone got any clues on where to start troubleshooting/fixing this issue ? I googled a bunch, and searched the forums, but found nothing that seemed relevant.

-- stan

---

### Post by CHaoSlayeR on 2009-12-12
According to this bug you are not alone:

[http://bugs.freedesktop.org/show_bug.cgi?id=20816](http://bugs.freedesktop.org/show_bug.cgi?id=20816)

And is still not fixed yet and as I watched the progress on those issues for quite some time now I think it is very unlikely that it get fixed for Ubuntu 10.04.

I'm suffering from that issue too since Intrepid. The xserver in Hardy was the last one that was able to do what it was written for. I hope they get it done fast. I have at least three monitors here standing around useless because of that.

If the Matrox drivers were any better (or if there were any open-source driver) I would go and buy one of those:

[http://www.matrox.com/graphics/en/products/graphics_cards/m_series/m9148lppciex16/](http://www.matrox.com/graphics/en/products/graphics_cards/m_series/m9148lppciex16/)

...or that one (for future expansion):

[http://www.matrox.com/graphics/en/products/graphics_cards/m_series/m9188pciex16/](http://www.matrox.com/graphics/en/products/graphics_cards/m_series/m9188pciex16/)

...imagine a wall of 8x 2560x1600 (!!!) 30" LCDs in two rows, spanning across a single screen with a viewport of 10240x3200 pixels (that is more than 30 MegaPixel). Although then you'll have to walk from one side to the other to see what's actually going on in the tail within that console... ;-)

...and AMD just got it managed to build a card that is capable of driving 3 of those cards at a time. And then take a look at the dimensions of the card and the power consumption...

Nevertheless, I hope that one day in the near future I can enable the additional cards in my systems again and finally use the rest of the monitors.

Cheers,

C]-[aoZ

---

### Post by Stanley Krute on 2009-12-12
> **CHaoSlayeR said:**
> According to this bug you are not alone:

[http://bugs.freedesktop.org/show_bug.cgi?id=20816](http://bugs.freedesktop.org/show_bug.cgi?id=20816)


Thanks C]-[aoZ for the update. I'm actually astonished at the Priority assigned
to this bug: Medium. For most serious computer users, it's a danged SHOWSTOPPER !!!

Installation issues of this nature are pretty much, imo, the key element holding
Linux back from widescale adoption

-- stan

---

### Post by CHaoSlayeR on 2009-12-12
It is medium because it doesn't prevent from using the software by itself. It's "just" some feature that is not working.

I also think the priority on that should be higher but in the end, I'm not an X dev. And in the meantime I try to get as many monitors driven with one card. That's some kind of dogma not put onto me by myself. And that is the fact I don't like.

C]-[aoZ

---


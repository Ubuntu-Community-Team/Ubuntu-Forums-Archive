---
title: "nVidia multiple TVs"
date: 2013-06-16
forum: Hardware
---

### Post by Fisher on 2013-06-16
Hello.
I have Ubuntu 10.04 + this videocard:

[http://wayback.archive.org/web/20090129211201/http://www.zogis.com/main_products_PCIE_ZO85GT-E.htm](http://wayback.archive.org/web/20090129211201/http://www.zogis.com/main_products_PCIE_ZO85GT-E.htm)

I have one VGA monitor plugged to it on the VGA port and a TV plugged on the SVideo port.
For the SVideo I'm using this adaptor:

[http://www.order-bulk.com/images/svideo_cablepc.jpg](http://www.order-bulk.com/images/svideo_cablepc.jpg)

My question is: is it possible to have a second TV plugged in this VideoCard through Composite Video using one of the Component Video outputs?
I want to have 2 old TVs plugged in with different contents.
I've seem some TVs that accept composite through one of the component inputs.
Is it possible to do it for output on this VideoCard?
Thanks!!

---

### Post by TiberiusT on 2013-06-16
Bom dia...I used to have an 8500GT. For sure it only supports 2 simultaneous outputs. 3 won't work - it will just pick 2 of them and abandon the 3rd. Does it have an S-Video output? I ask bcos that is the one to use with a standard S-Video cable to the TV. Otherwise if your TV only has composite input use a simple S-Video to composite converter, but S-Video will give significantly better quality. That cable looks like it's trying to get component video out of S-Video but my card did not support that - very few do adn they are nearly all ATI cards.
Also I wouldn't try and 'split' the TV output into 2 - you'll need an expensive amplifier otherwise the signal won't be high enough and you'll get crap output.

On Ubuntu though you can run 2 video cards which would give you 4 outputs - I'd update from 10.04 though. With NVidia cards the NVidia Settings GUI sets this up for you with different X-Screens.

Cheers
T

---

### Post by Fisher on 2013-06-17
So... it's not possible :-(
I already have another video card with similar chipset and two outputs.
Looks like I'll need another videocard...
Think an pci express x1 to x16 adapter may be the way to go...
I 'll try this adapter:

[http://dx.com/p/pci-e-1x-to-16x-riser-card-extension-cable-15-5cm-length-100061](http://dx.com/p/pci-e-1x-to-16x-riser-card-extension-cable-15-5cm-length-100061)

Not sure how I will put the videocard inside the pc...

---

### Post by TiberiusT on 2013-06-18
I've done quite a bit of this twin video card and TV-out stuff. Sometimes it works...perfectly, forever...sometimes X11 just refuses. Keep the setup as standard as possible to maximise chances of success. 2 x NVidia PCI-Ex16 cards in two PCI-Ex16 slots is the way to go - I'll be verrrrryyyyyy surprised if it works through that adapter. 

T

---

### Post by Fisher on 2013-07-07
I tried a 3rd monitor. First it just says it doesn't support the required metamode and don't start the second monitor. Other times it silently ignores the second monitor.
I'm using the 283.13 version of the nvidia drivers because the newer one don't allow me to do multiseat.
I have another question, maybe it should be in another thread: If I update my ubuntu machine to the latest lts and drivers, will I be able to keep my multiseat setup?
The only problems I'm having right now is with flash being finicky and crashing most of the time in firefox... I Just can't make tvtime work either (3x usb soundcards, for the other 3 seats), but I think it's not the right place to complain...

---


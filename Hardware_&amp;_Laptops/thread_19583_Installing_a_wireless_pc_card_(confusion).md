---
title: "Installing a wireless pc card (confusion)"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by augereffect on 2005-03-12
I'm new to linux and am trying to figure out how to install a wireless PCMCIA card on my laptop.  Right now, i have a linksys card.

I'm wondering:

- will this card work?
- if not, what kind of card will (non PCMCIA necessary?)
- how do i go about installing it

could someone please give me a blow by blow of this?

thanks

---

### Post by deception on 2005-03-12
Which model is the card? 

Normally, you need to insert the card into the PCMCIA slot, boot up Ubuntu, connect the laptop by Cat5/5e/6 cable to the WAP, open Synaptics, search for "ndiswrapper" mark for installation, apply 

then go to [http://ndiswrapper.sf.net/wiki](http://ndiswrapper.sf.net/wiki) and follow the setup instructions, excluding the install instructions. 

Then you should be good to go  =D>

---

### Post by burlap on 2005-03-12
Well, first go to [this Ubuntu wiki page](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards). 

If your card doesn't work out of the box it is very probable you'll in fact need ndiswrapper (however, let's assume that the rule is to avoid it). 

Actually, I use ndiswrapper (no WEP for acx111).

---


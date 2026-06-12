---
title: "Best wireless card for linux?"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by wr0x2 on 2005-12-27
I am thinking of getting a new wireless card for my wardriving box. Here are the criteria that it must meet:

Very well supported chipset capable of moniter mode, scan mode, etc. (I was thinking prism2)
Antenna connector is a must.
Card only has to support 802.11b. Money is a factor in my decision, and I do not need G or A support.
Also, the card would preferably be a 5v card, since at the moment that is all that my laptop supports.


I would probably buy the card used from ebay, so older or discontinued models are not out of the question.

---

### Post by bernardfrancois on 2005-12-27
I bought an Cisco Aeronet 350 series card on ebay. Cisco has it's own linux driver for it (afaik it is the only wlan card for which the manufacturer itself made a linux driver and linux utilities).

I didn't need to install any of the drivers or tools, so I never tried it. I just inserted the card and that was it; it worked... It seems to automatically pick the strongest unprotected wireless network. Since my wireless network only has MAC-adress based protection, it works fine. Same for the network of my parents...

Note that there are different versions of those cards. Some have a built-in antenna, others (like mine) have two mmcx connectors. Often an antenna for the version without antenna is not included in the sale at ebay.

---

### Post by SavageBeginner on 2005-12-27
You may want to check out this page:  [http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

---

### Post by valnar on 2005-12-28
[QUOTE=SavageBeginner]You may want to check out this page:  [http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)[/QUOTE]

I've never seen that list before until now, but I have to disagree with it.  Atheros based cards would be my preference, and Intel cards (or the chips in the 802.11b Centrino) work fine in Linux too.

'Nothing against FSF, but they're spreading FUD.

Robert

---

### Post by moopere on 2005-12-31
[QUOTE=valnar]I've never seen that list before until now, but I have to disagree with it.  Atheros based cards would be my preference, and Intel cards (or the chips in the 802.11b Centrino) work fine in Linux too.

'Nothing against FSF, but they're spreading FUD.

Robert[/QUOTE]

I can't comment on the Intel card, but you can't honestly say the FSF is spreading FUD in relation to the Atheros units.

They are telling the truth as far as Atheros cards go, I have a couple, I know.

You do indeed need a 'binary blob' which is not open source in order to make these cards work (which is wrapped up in the madwifi effort as described on the FSF site).  

It just so happens that right now all is well and the blob integrates ok with current kernels.  Don't expect this to necessarily continue into the future though - if a newer kernel breaks something that needs fixing in the binary blob and if by then Atheros is not interested in supporting an old product you'll have to throw the card out - thats the point of getting the source code - its a level of security that goes beyond the OEM.

Whilst my card works and works well, I won't be buying into products with (only) closed source drivers again, far too much of a risk (what exactly _does_ that piece of precompiled code do?  Hmm?) and just downright bad practice for Linux lovers/users.

Cheers,
Craig

---

### Post by gl0wst1ckn1nja on 2007-08-01
i just bought an atheros 6G dcma 82 card for my laptop mPCI slot and it works flawlessly with my linux machine.  madwifi is very easy to install ... get the tar file and extract it ... cd to the directory and sudo make ... thats it it works amazingly ... the built in antenna sucks but with the mmcx antenna its amazing.  the range is unbelievable

and it supports turbo and speed boost

---


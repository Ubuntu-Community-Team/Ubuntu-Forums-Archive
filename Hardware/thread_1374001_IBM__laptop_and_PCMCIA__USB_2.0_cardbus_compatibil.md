---
title: "IBM  laptop and PCMCIA  USB 2.0 cardbus compatibility issues"
date: 2010-01-06
forum: Hardware
---

### Post by puteruser on 2010-01-06
I have a refurbished IBM A31 laptop with Windows 2000 professional and a couple of months ago I accidentally shorted out one of the USB ports and now neither one works.  I bought a PCMCIA USB 2.0 card off eBay and it detects the card but the recommended driver has a exclamation marker on it in the device manager.  I've already tried all the driver combinations and some will install without the exclamation marker but it still won't detect any devices I plug into it.  The brand of the card is a very generic cheap brand that came from Hong Kong for like 7 dollars and it came with a driver CD and I've tried every driver on that CD.  The card has a plug in the center for a round plug which fits the cord that was included.  One thing I was wondering is does the cord have to plugged into the round plug and one of the USB's in order to work and if not what was this cord intended for?

---

### Post by puteruser on 2010-01-06
I know this laptop is ancient and most wouldn't bother fixing it but I need to fix it so I can sell it so please I would appreciate any kind of advice.  THANKS.

---

### Post by muranyia on 2010-03-16
Other than that, this is a forum for Ubuntu linux users.
:popcorn:

---

### Post by tgalati4 on 2010-03-16
Burning out the 5V rail is probably causing the pcmcia card not to work properly either.  USB is supposted to put out 5 VDC at 1/2 an amp.  With 4 ports, that's 5 VDC at 2 amps.  Since the 5 VDC power rail got shorted and probably blew a fuse on the motherboard, any device requiring regulated 5 VDC power will probably not work.

You can repair the board.  There are instructions on the web for how to dismantle and solder in a new fuse.  It's not easy.  Or just sell it as is with the disclaimer.

---


---
title: "Trouble with Netgear FA411 Ethernet card"
date: 2009-04-12
forum: Hardware
---

### Post by AdjectiveCreature on 2009-04-12
I'm having trouble with a friend's Netgear FA411 Ethernet card in his old Dell Inspiron 3800 laptop, which has no built-in RJ-45 jack.  It works perfectly in my Acer TravelMate 5520, so I suspect there may be a driver or other problem with his PCMCIA bus.

When we insert the card and plug in an Ethernet cable, the LEDs on the card light up but do not blink.  ifconfig -a fails to detect the device.  lspci finds a Texas Instruments PCI1225 CardBus bridge with the yenta_cardbus driver enabled, but it doesn't seem to detect the card.

Any suggestions?  It's difficult to post detailed logs as I can't access the Internet from the Dell laptop until we solve this problem...

Thanks!

---

### Post by schmidtbag on 2009-04-13
post the results of lsmod, and lspcmcia.  you can save the information to a flash drive or floppy disk if that helps send the information.

---


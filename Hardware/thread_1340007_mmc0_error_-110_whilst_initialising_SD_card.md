---
title: "mmc0: error -110 whilst initialising SD card"
date: 2009-11-28
forum: Hardware
---

### Post by 00chilli00 on 2009-11-28
Hi 
Can anyone help im trying to load a SD card
but get mmc0: error -110 whilst initialising SD card
lspci gives me 
07:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


Im running 9.04 Lenovo ideapad Y530

---

### Post by psytrox on 2010-01-12
I have the same issue.  Mine output reads:

[  195.653032] mmc0: error -110 whilst initialising SD card


This card was in a pocket when the holder fainted, and possibly hurt the card physically.  Since it worked completely fine, just prior to this, the only solution I've read that may work, is splitting the card's case open, and re-soldering the contacts.  Any ideas?  Thanks!

---


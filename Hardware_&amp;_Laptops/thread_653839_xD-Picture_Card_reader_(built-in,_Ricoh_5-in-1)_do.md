---
title: "xD-Picture Card reader (built-in, Ricoh 5-in-1) doesn't work"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by martinquested on 2007-12-30
Hello.

My built-in 5-in-1 Card Reader works great with SD cards but it doesn't seem to like xD cards.

My research so far tells me that SD cards have been more successfully dealt with in Linux, and xD cards are problematic, because the format is proprietary and only really being used by Olympus these days.  However, I also know that there is a downloadable Windows driver available for this card reader so presumably it is theoretically possible to reverse engineer it?  (I have no idea about doing something like that, unfortunately.)

Does anyone know if it is possible to use the Windows driver, or if a Linux driver is on its way, or if indeed a solution already exists?  Or will a future kernel support the xD cards out-of-the-box?

Oh, yes, my lspci:

07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Thanks in advance!

---

### Post by arqbrulo on 2008-01-15
Same issue here. Do you happen to have a Dell computer? I just bought one and when I insert the xD card, nothing. I have not tried other types of memory cards, 'cause xD is the only one I use. BTW, I have a built-in Ricoh 8-in-1.

---

### Post by martinquested on 2008-01-15
No, mine's a Compaq Presario V6030US (V6000 series)

---

### Post by jgoguen on 2008-01-15
I have a HP Pavilion dv2622 with a 5-in-1 card reader (SD, Memory Stick, MS Pro, MMC, xD) that doesn't work properly.  SD works fine, but for anything else it's like I never inserted a card to begin with.

01:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by doorknob60 on 2008-03-24
I'll bump this. I have a HP Pavilion dv9008nr and it works fine with SD but not xD :( i'd like to see a solution. Maybe in Hardy :D?

---

### Post by martinquested on 2008-03-24
My solution has been to buy a USB-stick xD card reader on ebay.  It cost a mere GBP 3.00 including postage from Hong Kong, and it does the job.  Shame to have to have a workaround though.

---


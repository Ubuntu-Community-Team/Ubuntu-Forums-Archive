---
title: "sd card reader freezes computer during live cd session"
date: 2009-12-21
forum: Hardware
---

### Post by MichaelBurns on 2009-12-21
I killed my harddrive, so I am just running off of a live cd of ubuntu 9.04.  I want to transfer some pictures from my sd card to a flash drive.  My usb's seem to be working fine, but my laptop freezes when I put the sd card in the slot.  Does anyone have an idea why?

from lshw:
```

           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7 module=tifm_7xx1

```

---

### Post by MichaelBurns on 2009-12-28
UPDATE:
I was able to connect my camera through usb to get the pictures onto a flash drive, so I'm guessing that there is nothing wrong with the sd card.  Still, for future reference, I would like to understand why the card reader doesn't work from the live cd, if for no other reason than it will help me to better understand how ubuntu works.

---

### Post by MichaelBurns on 2010-01-26
bump

---

### Post by llawwehttam on 2010-01-26
The live cd is very slow and can be a bit weird at times. It may be trying to mount it to a folder that doesn't exist or something. If I want to do something like this I use knoppix because its designed just to be used live.

---

### Post by MichaelBurns on 2010-04-14
bump

---

### Post by MichaelBurns on 2010-06-28
bump

---


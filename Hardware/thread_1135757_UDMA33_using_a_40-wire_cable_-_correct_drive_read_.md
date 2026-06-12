---
title: "UDMA/33 using a 40-wire cable - correct drive read speeds? using hdparm"
date: 2009-04-24
forum: Hardware
---

### Post by frammy7 on 2009-04-24
I'm trying to work out if I'm getting the best speed I can out of my HDD as my system can be a little slow somedays... (I'm using hdparm to test the read speed)..

The system (xubuntu 8.04) is running from a 133x Compact Flash Card, connected by a 40-wire cable to the motherboard.

my dmesg states:
```
[   24.610923] ata1.00: ATA-4: ELITE PRO CF CARD 4GB, 20071207, max UDMA/66
[   24.610934] ata1.00: 7831152 sectors, multi 0: LBA
[   24.610958] ata1.00: **limited to UDMA/33 due to 40-wire cable**
[   24.627191] ata1.00: configured for UDMA/33
[   24.627281] ata2: port disabled. ignoring. 
```

I have found other people referencing a bug with what UDMA mode Ubuntu 8.04 recognises, and my hdparm -i for the drives states:
```
UDMA modes: udma0 udma1 *udma2 udma3 udma4
Drive conforms to: Unspecified:  ATA/ATAPI-4 
```

...and obviously it isn't managing to use UDMA4 / ATA4 - but **am I to assume that as I *AM actually* using a 40-wire cable, that UDMA/33 is the best I will ever get out of it? Can a 40-wire cable go no faster? As I was thinking of replacing the card with a 266x speed one?**



Also, my hdparm -tT dev/sda1 gives:
```
Timing cached reads:   356 MB in  2.00 seconds = 177.91 MB/sec
Timing buffered disk reads:   66 MB in  3.04 seconds =  21.74 MB/sec 
```
Are these speeds reasonable - or is it likely to be causing things to run a little slowly**?**

Bit of a n00b question I'm sure - so apologies!

---

### Post by cabbage on 2009-10-11
You've probably worked this out already - but I just stumbled across this... What you need is an 80 wire IDE cable. Then you can go upto udma6 (if your controller supports it).

---


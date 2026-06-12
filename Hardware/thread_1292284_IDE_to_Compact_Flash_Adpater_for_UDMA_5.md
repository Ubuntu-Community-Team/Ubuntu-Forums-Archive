---
title: "IDE to Compact Flash Adpater for UDMA 5"
date: 2009-10-15
forum: Hardware
---

### Post by cabbage on 2009-10-15
Hi,

I've just brought a Transcend 600x 8GB compact flash card that I'm intending to use as the OS disk for my mythbuntu system with the aid of an IDE to CF adapter.

This card supposedly transfers data at 90MB/s but my first attempt to use it produced random speeds ultimately ending up with the system becoming unusable.

I've figured that was due to the cheap IDE to Cf adapter not supporting DMA.

So now I want to buy a new one that will work and at full speed (in this case udma 5)...

I've found this page which talks about the problems:

[INDENT][http://www.e-consystems.com/operatingCF.asp](http://www.e-consystems.com/operatingCF.asp)[/INDENT]

According to this I need to have the right pins connected, with resistors and grounding lines!

I've also discovered that for my card to operate at speeds greater than udma 4 it must be run at 3.3V (this is buried in the product's  datasheet).

So the nearest adapter I've found to that is this one (it at least has switchable voltage - not sure about the crosstalk issue):

[INDENT][http://www.startech.com/item/IDE2CF-40-44-pin-IDE-to-Compact-Flash-SSD-Adapter.aspx](http://www.startech.com/item/IDE2CF-40-44-pin-IDE-to-Compact-Flash-SSD-Adapter.aspx)[/INDENT]

My question is (well done if you're still reading) before I spend any more money has anyone else got a card working at this speed and with what adapter?


Thanks,

Cabbage.

---

### Post by cabbage on 2009-10-16
Just found this:

[INDENT][http://www.hjreggel.net/cardspeed/cs_udmacf.html](http://www.hjreggel.net/cardspeed/cs_udmacf.html)[/INDENT]

So now I can only have one device on the bus and a max cable length of six inches..!

---

### Post by cabbage on 2009-12-03
I finally opted for the Startech adapter but then my CF died!

I returned it under warranty and have just got a replacement - which works nicely.

A "hdparm -it" gives:

```
/dev/sda:

 Model=TRANSCEND                               , FwRev=20090907, SerialNo=20091005    0000053D
 Config={ HardSect NotMFM Fixed DTR>10Mbs }
 RawCHS=15538/16/63, TrkSize=0, SectSize=576, ECCbytes=4
 BuffType=DualPort, BuffSize=1kB, MaxMultSect=1, MultSect=?0?
 CurCHS=15538/16/63, CurSects=15662304, LBA=yes, LBAsects=15662304
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled

 * signifies the current active mode

 Timing buffered disk reads:  214 MB in  3.01 seconds =  71.19 MB/sec

```

So although its not the advertised 90MBs its still not bad and its talking to the controller at 133MBs udma6!

---


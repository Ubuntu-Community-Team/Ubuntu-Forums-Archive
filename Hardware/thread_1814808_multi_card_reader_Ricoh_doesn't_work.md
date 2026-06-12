---
title: "multi card reader Ricoh doesn't work"
date: 2011-07-30
forum: Hardware
---

### Post by brianthechem on 2011-07-30
on an Acer Aspire 4520 with Ubuntu 10.04 LTS the card reader doesn't work.
writing these commands on Terminal the results are:
```
lsusb
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a41 Dexon 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and for ```
lspci | grep Ricoh
```

01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

How does it work?

Thank you and sorry for my bad english

---

### Post by coffeecat on 2011-07-30
Are you using a SD or SDHC (SD high capacity) card? Some (but not all) card reader chipsets will not recognise a SDHC card with the Linux driver. If you were trying with a SDHC card, try a lower capacity SD card to see if the actual card reader is working.

---

### Post by brianthechem on 2011-07-30
i have to use a Sony Memory Stick.
I don't have any problem wit an SD card.

---

### Post by brianthechem on 2011-08-02
I used this driver [http://gitorious.org/ricoh-kernel](http://gitorious.org/ricoh-kernel) without positive results.
Can you help me?

---

### Post by coffeecat on 2011-08-02
I never bothered to try to get a Sony memory stick to work, even on a Sony laptop, so I wouldn't know where to start with that. Sorry.

---

### Post by brianthechem on 2011-08-02
thank you.
I resolve the problem on the italian ubuntu-forum.
[http://forum.ubuntu-it.org/index.php/topic,473771.0.html](http://forum.ubuntu-it.org/index.php/topic,473771.0.html)

---

### Post by TSMJ on 2013-03-09
Hello,

For anyone having trouble with a Lenovo X61 and Ubuntu 12.04, I had to enable the SD card slot in the BIOS before it would work.

---

### Post by coffeecat on 2013-03-09
Back to sleep, thread.

---


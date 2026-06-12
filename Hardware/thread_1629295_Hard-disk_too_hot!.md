---
title: "Hard-disk too hot!"
date: 2010-11-23
forum: Hardware
---

### Post by ario on 2010-11-23
I can't use my touchpad because it's burning my fingers! The source for this huge temperature which can melt some candles is my hard drive.
Heres the out put of hddtemp command:
```
ario@ario-laptop:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD3200BEVT-22ZCT0: 59°C

```
Can't use hdparm -B because whatever I put in front of B it will spin down my hard drive in only five seconds, which is too bad! (Searched for it a lot, and found that linux can not solve this problem for my hard drive. So forgot about it!).
How can I cool down the hard drive?
I now that my hard drive will stop working in next months if I don't do anything for it:(
Please help. Any response will be appreciated.

---

### Post by ario on 2011-03-09
Bump!

---

### Post by Yellow Pasque on 2011-03-09
Install atop package to see what's accessing the disk so much. Also, look at startup programs and disable anything unnecessary.

---

### Post by doas777 on 2011-03-09
can you confirm that temp via the Disk Utility's SMART data? 

my guess is that the OS has less to do with whatever is generating the heat (friction perhaps?) than does a hardware problem. check your SMART stats to see what the health of your drive is.

---

### Post by Markus72 on 2011-03-09
Hi,

I just googled a bit because I was curious. I found several posts describing high temperatures for that particular hdd model.
Plus, some laptop models currently became "warmer" especially regarding the hdd temps when compared to older ubuntu releases.

I have a Lenovo T500 also with a WDC disc but a different model and I stressed it now for quite a while:

```
/dev/sdb: WDC WD3200BEVS-08VAT2: 44°C
```

Before starting the test, it was at about 37°C idling... now after end of the test it is at 42°C idling...

Just being curious - is the hdd being accessed permanently or is it idling (which would surprise me)?

You don't have Windows installed as well? No experience wheather this is really a ubuntu problem or a general issue?
Frankly, I'm no pro regarding these things but I made some really annoying experiences with power management / cooling related to bad laptop firmware/bios software (and I'm talking about a 1.300€ Asus laptop - no cheap crap) ;-)

What HW do you use?

Markus

---


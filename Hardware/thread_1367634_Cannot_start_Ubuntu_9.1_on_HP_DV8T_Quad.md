---
title: "Cannot start Ubuntu 9.1 on HP DV8T Quad"
date: 2009-12-29
forum: Hardware
---

### Post by theegyptianwarrior on 2009-12-29
I have the HP DV8T Quad Edition laptop with the following specs:
• Genuine Windows 7 Home Premium 64-bit
• Intel(R) Core(TM) i7-720QM Processor (1.6GHz, 6MB L2 Cache, 1333MHz FSB)
• 4GB DDR3 System Memory (2 Dimm) 
• 320GB 7200RPM SATA Hard Drive with HP ProtectSmart Hard Drive Protection
• 1GB Nvidia GeForce GT 230M
• 18.4" diagonal High Definition HP Ultra BrightView Infinity Display (1920x1080p)
• Lightscribe Blu-Ray ROM with SuperMulti DVD+/-R/RW Double Layer
• Webcam + Fingerprint Reader
• Intel Wireless-N Mini-card (Intel AGN 5100)

I burned an Ubuntu 9.1 32-bit boot up disc and I ran it. It brings the loading bar that slides back and forth and has no problem finishing. But, the final loading bar that fills up as it completes loading stops only after filling up slightly. I also hear the DVD stop spinning. I tried using an older version of ubuntu but the same exact thing happens. Any help would be appreciated.

---

### Post by bherrmann7 on 2010-03-29
I have one on order.  Should arrive next week.   Seems someone got it up and running....

     [http://www.linlap.com/wiki/hp+pavilion+dv8t+quad](http://www.linlap.com/wiki/hp+pavilion+dv8t+quad)

-bob

---

### Post by bug67 on 2010-03-29
I have this laptop.  I installed and booted 9.10 (*64 bit*) without problems except:

1.  No wifi.  Probably coulda spent some time with ndswrapper and got it working but, I didn't feel like it.

2.  Sound would *only* come out of the unit's sub-woofer.  Zero sound from head phone jack.  

Same issues when I tried Linux Mint 8 (Helena) on this machine.

So, I downloaded and booted from the 10.04 B1 Lucid LiveCD:

1.  Wifi worked flawlessly.  No ndswrapper required.

2.  Sound now plays through all internal speakers.  Still no head phone out though.

Sorry I can't give you any help as to why yours isn't booting.  I don't *think* not running 64 bit would have any thing to do with it but, you never know.  Possibly a bad iso burn.  Did you burn at the slowest possible speed?  Did you do an md5sum?

---

### Post by bherrmann7 on 2010-03-29
When installing Ubuntu on a new machine, I always recommend running the "Check CD for defects" and then running the "Memory test" for an iteration or two.  

       [http://www.psychocats.net/ubuntu/images/virtualbox33.png](http://www.psychocats.net/ubuntu/images/virtualbox33.png)

This can save you some bad media and or bad memory/system headaches.

---


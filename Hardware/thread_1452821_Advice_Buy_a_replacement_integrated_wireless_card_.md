---
title: "Advice: Buy a replacement integrated wireless card or go for PCI/USB external card?"
date: 2010-04-12
forum: Hardware
---

### Post by fifth_rune on 2010-04-12
After a few weeks trying to resolve why my wireless stopped working, I have confirmed that it is not a software/driver issue but a hardware issue.  Trouble is, I'm not sure if the card is faulty or if there is something else going on (i.e. antenna wires malfunctioning, etc).  So right now I am trying to decide if I should get a new replacement card or just get a PCI/USB external wifi card. If I get a replacement card and it isn't the wireless card that was the issue, I have essentially wasted some money and time.  If I get the PCI/USB external wifi, I am almost certain that will work, but it is not an ideal solution (range is crappier by all accounts, drains more power, and looks ugly sticking out of my system, esp. the models that have antennas).  Any particular advice about what would be the better choice?  Here are some relevant facts:

- Dell Inspiron E1405 laptop with Broadcom 1428 wifi card
- Wireless is detected, power goes to it, the lights are on, etc.  However the malfunction is that it does not 'scan' for networks so it essentially doesn't work.  
- Occaisionally (very rarely, every few days) functionality returns for a little while, from a few seconds, to almost a whole day before leaving for almost no apparent reason as well.

Any thoughts or suggestions would be greatly appreciated.

---

### Post by conradin on 2010-04-12
Honestly Ive never seen the internal antennas break, there are simply no moving parts there, and they often have auxiliary antennas. If you watch the boot sequence instead of the splash screen during boot, sometimes you can find errors in there that may alert you into what is not working. I would be interested to know if the hardware is still identified in lshw when it isn't working. 

Im also curious about any switches that might turn the device off 
many laptops have such things.

Personally i like to fill the inner slots before the exterior slots. a PCMCIA slot could be used for something else someday.
I think you need to know whether you have a full PCI or the mini PCI slot. (Im assuming you might not get the same model you had)

---

### Post by fifth_rune on 2010-04-12
> **conradin said:**
> Honestly Ive never seen the internal antennas break, there are simply no moving parts there, and they often have auxiliary antennas. If you watch the boot sequence instead of the splash screen during boot, sometimes you can find errors in there that may alert you into what is not working. I would be interested to know if the hardware is still identified in lshw when it isn't working. 

Im also curious about any switches that might turn the device off 
many laptops have such things.

Personally i like to fill the inner slots before the exterior slots. a PCMCIA slot could be used for something else someday.
I think you need to know whether you have a full PCI or the mini PCI slot. (Im assuming you might not get the same model you had)


Boot sequence is clean.  Hardware is identified and proper in lshw.  I am aware of the annoying switch to turn wifi on/off for this model and it is not an issue.  The wifi is detected by the system for sure, I even went and installed Windows on it with the supported, factory drivers to be sure and it picked up just fine, just can't 'scan' for available networks to connect to.  

So, if the antenna rarely breaks, do you think I just somehow fried my current internal wifi card?  Just curious.

---


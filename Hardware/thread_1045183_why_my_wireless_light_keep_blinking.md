---
title: "why my wireless light keep blinking"
date: 2009-01-20
forum: Hardware
---

### Post by egypro on 2009-01-20
i have installed ubunto 7.4 and it was ok then i formated and reinstall ubunto 8.10 every thing still ok exsept that my wireless light keep blinking ,i know ifr the light is off so the wireless is off and if on card is on , it blinks very quickly internet still working but i need to know what does that mean
i have dell inspiron e1505 with ati graphic card 256 and duel core 1.6 cpu
also i wanna know 
what is the diffrent between hda and sda i know that is hard disk name in command line but what is the diffrent

---

### Post by squaregoldfish on 2009-01-20
The blinking light is a new feature in 8.10 - it blinks when the connection's in use. The blinking can be disabled if you don't like it - see here:

[http://ubuntuforums.org/showthread.php?t=1017700]("http://ubuntuforums.org/showthread.php?t=1017700")


hdx and sdx are different ways of referencing storage devices. hdx indicates a plain IDE device. sdx indicates a SCSI device. However, a lot of storage devices (eg SATA and USB) are accessed through the SCSI system, so they're listed as sdx as well.

Steve.

---


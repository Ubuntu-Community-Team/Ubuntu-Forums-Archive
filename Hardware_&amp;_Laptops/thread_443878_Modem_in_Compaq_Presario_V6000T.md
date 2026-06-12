---
title: "Modem in Compaq Presario V6000T"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Riom on 2007-05-14
Has anybody got the modem in the Compaq Presario V6000T (or the V6000Z if it's the same modem) to work with Ubuntu 7.04?

The modem appears to be a Conexant HSF Modem, vendor 14F1 device 5045

I've followed various "howto's" that seem mostly to have been written for much earlier versions (for example, for compiling from source I'm required to make sure I have GCC 3.4 - since I already have GCC 4.1.2 am I supposed to downgrade somehow, or was that written when GCC 3.4 was new?).  

Couldn't get sl-modem to compile as in [https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink) - maybe what's needed has changed for 7.04?

Tried the linuxant driver - that just kills the volume control and restarting the volume control kills the driver (looks like the modem, sound card and alsa are really closely interlinked).

For the first time with this computer, I'm going to be in a place with just dial up for a few weeks.  It would be nice to get the built-in modem to work, but after several hours of messing around it looks like the answer is going to be to buy a USB modem. :-(  

Pity, as this is one of the few things not working on this laptop under Ubuntu (that I've tested).  So, has anybody with this modem managed to get it to work at all?  Thanks!

---


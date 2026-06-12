---
title: "driver   GeForce 6600 GV-NX66128DP"
date: 2017-03-16
forum: Hardware
---

### Post by heian on 2017-03-16
Hi,

I got a GeForce 6600 GV-NX66128DP  card, that will be installed on an elder Ubuntu 16.04  computer. 
(motherboard  K9AGM3    MS - 7367   ver: 1.1 )


I really need  advice what is the best driver for this card, after a clean install of 16.04.
Is it best to do nothing at all, (beside switch off the motherboard vga), or is it better to install a proprietary driver. (the suggested one from Ubuntu hardware, or from nVidia  website?
Or what do I type in the terminal, to get the best driver?

I love to use Ubuntu, but not really keen on playing around with drivers or in the terminal.

Thanks in advance for any help!

heian


( [https://www.czc.cz/gigabyte-geforce-6600-gv-nx66128dp-turbo-128mb-pci-e/30528/produkt](https://www.czc.cz/gigabyte-geforce-6600-gv-nx66128dp-turbo-128mb-pci-e/30528/produkt))

---

### Post by howefield on 2017-03-16
I believe the 304.134 driver that you would be offered in 16.04 (additional drivers) supports your card.

I'd suggest running with the open source driver installed by default for a while, if it suffices then fine. If you have glitches or poor performance then try the above driver.

I'd steer away from the nvidia website driver given your reluctance to fix it when it goes wrong ;)

What are you using the computer for ?

---

### Post by mörgæs on 2017-03-16
Hi, I suggest that you begin with installing X/Lubuntu using the default open source drivers. Run it for some days and post again if the graphics are too slow.

(ninja'ed by Howefield)

---

### Post by heian on 2017-03-16
It will be used for simple web-browsing, youtubing, checking mail and so on.
Definite not for gaming and so on.

---

### Post by howefield on 2017-03-16
So, sounds like the most taxing duty may be the Unity desktop itself and playing some video. You may well find that the default installed open source driver will suffice but if you get a choppy poor performance, then as above, additional drivers should give you a supported driver. There is really only one way to find out :)

Personally I'd always use the proprietary drivers offered for best performance. Also, installing them from the "additional drivers" application will ensure updates are applied should there be any. Installing from the nvidia website means that you are pretty much on your own with a high chance of breakage at the next kernel update.

---


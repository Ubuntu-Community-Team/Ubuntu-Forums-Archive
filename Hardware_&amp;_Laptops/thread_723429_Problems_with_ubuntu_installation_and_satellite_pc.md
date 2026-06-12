---
title: "Problems with ubuntu installation and satellite pci card"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by rosponius2 on 2008-03-13
Hi to all I am a newbie!
I've tried to install ubuntu on my desktop pc but found a problem with my pci satellite card, a dexatek sphere dk-5701.
When ubuntu begins the verification of hardware configuration, it stops and gives me an error any time it tries to recognize my sat card.
This is the error it gives: bttv0:subsystem 0000:2001.
So I tried to remove the card and install ubuntu without the card, everything worked fine, than of course when I reconnect the card ubuntu doesn't even start. I tried to find some drivers and solution on google searches but couldn't find anything.
Now I wonder if there's a way to solve this problem. I don't care if I can't use the card on ubuntu, I use it on windows on an other partition. Anyway I want at least be able to start ubuntu without having to unplug the card anytime!!: is there a way to disable the pci card in some ways on ubuntu? Thanks

---

### Post by rosponius on 2008-03-19
:)
Hello I added the following lines in this file: etc/modprobe.d/options (thanks to an italian ubuntu forum user who suggested this solution for a twinhan card, it works also for my dexatek):

options dvb_core dvb_shutdown_timeout=0
options bttv i2c_hw=1 card=0x71

Don't know what they means, dont' know if the card works (I didn't try yet) but at least now I can boot my ubuntu!:)

---


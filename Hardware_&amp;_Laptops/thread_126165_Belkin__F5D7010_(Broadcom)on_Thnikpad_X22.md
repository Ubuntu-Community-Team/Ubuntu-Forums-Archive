---
title: "Belkin  F5D7010 (Broadcom)on Thnikpad X22"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by ivanhelguera on 2006-02-05
Hi, 
I was trying to make my belkin PCMCIA (cardbus, actually) card working on my X22 thinkpad/Kubuntu 5.10 with this guide
[http://ubuntuforums.org/showthread.php?t=25683&highlight=wireless+pcmcia](http://ubuntuforums.org/showthread.php?t=25683&highlight=wireless+pcmcia)
So :
ndiswrapper -l shows both hard&soft present

KinfoCentre does not list any PCMCIA cards. However, the card is found under PCI (together with cardbus bridge). 
For some reason, ethernet is listed as available only to root. 't be I Kcontrol, network interface include only eth0, disabled , and which cant be enabled (it's not plugged anywhere, though)
when I ```
sudo modprobe ndiswrapper 
```
the light goes green for a depressingly short time. 
Any ideas, anyone?

---

### Post by ivanhelguera on 2006-02-05
Meanwhile I made  a big step forward - actually, my X22 is currently upgradeing the Kubu5.10 over the wireless. The large part of the problem was that the it seems necessary to use bmclw.5a driver - i.e. one which is supposed to be designed for W95/98. I still have some problem with the WEP, but that's another story...
best IH

---


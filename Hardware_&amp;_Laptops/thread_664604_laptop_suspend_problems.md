---
title: "laptop suspend problems"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by sunfish on 2008-01-11
I'm running Edgy on an HP Omnibook 800CT.  Most things work just fine (albeit slowly) but I'm having problems with suspend. 

If I suspend (using sudo apm -s) with line power and bring it up still connected to line power, everything is fine.

If I try suspend on battery power, it will suspend, but comes back in a hung state. Connecting line power to come back from suspend makes no difference. What really seems to happen is that the hard drive fails to come up.

I have tried 'pccardctl eject' before suspend (on battery) and the laptop WILL come up OK. BUT as soon as I 'pccardctl insert' the machine hangs. 'pccardctl insert' DOES work as long as I don't actually suspend the machine.

Do I have any suggestions? This machine runs on a P166 with a max of 80mb ram. What irks me most about this problem is that when I was running WinXP on this machine it WOULD suspend properly. I should be able to do it with Linux. Gosh, I hope so, Windows is such a bore!

---

### Post by sunfish on 2008-01-19
After further investigation:

What seems to cause the machine to hang is the act of inserting the wireless network card after the machine has been suspended on battery power. This is done either by 'sudo pccarcctl insert' or physically inserting the card in an empty pccard socket. So something that hotplug or pccardctl does to power up the network card hangs the system.

I have looked in all the logs I can find and nothing seems to indicate any fatal errors. I have also tried unloading kernel modules specific to the wifi network card prior to inserting the card, but it changes nothing. This is very frustrating.

---


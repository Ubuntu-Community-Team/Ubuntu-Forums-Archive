---
title: "How to blacklist the pci id in hotplug"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by rosponius on 2008-03-16
I have a problem with a dexatek pci sat card (the dk-5701 card)
I don't care if this card doesn't work with linux kernel, I will use it with windows, but the problem is that ubuntu doesn't even boot when I have this card plugged in. I found some information on a linux dvb support site on how to disable the card :
[http://www.spinics.net/lists/linux-dvb/msg12546.html](http://www.spinics.net/lists/linux-dvb/msg12546.html)

"I recommend all linux(/xp dual boot) users who want to plug this card in even for use on windows only to add "alias bttv off" to /etc/modprobe.conf or in an extra file /etc/modprobe.d/dvb or **better blacklist the pci id in hotplug in between to get linux to boot again as emergency measure**, *before* you plugin this card."


Now as I am a real noob at ubuntu, I wonder what is the procedure to blacklist the pci id in hotplug, and I don't  know what it is the pci id (is it perhaps the irq number?).
So if anyone could help with this procedure I would appreciate.
Another noob question: the "alias bttv off" command in modprobe file is it to be written with or without the quotation marks?
thanks

---


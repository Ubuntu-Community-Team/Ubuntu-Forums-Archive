---
title: "New mini PCI wireless card advice"
date: 2012-08-29
forum: Hardware
---

### Post by Bobisha on 2012-08-29
I own a Dell Inspiron 6000 with Ubuntu 11.10, and I am in the process of updating some of the hardware little by little because I don't have the money right now to buy a new one. I am looking to upgrade my wireless card. Right now I am running on the broadcom 4318 a/b/g card. The main thing right now that I am trying to figure out is if the [SIZE=2]Broadcom BCM43222 4322 mini PCI 802.11a/b/g/n A241-431801R-02 Dual Band Wifi Wireless Card 300M[/SIZE] is compatible with my laptop. I was able to find a few good deals on this card, and it seems to be the best bet for an upgrade. If this is not a compatible upgrade, can someone recommend one for me? Thanks.

---

### Post by ahallubuntu on 2012-08-29
It worked for this guy in Windows:

[http://forum.notebookreview.com/dell-inspiron-dell-studio/648578-need-some-help-finding-drivers-dell-inspiron-6000-broadcom-bcm4322-wlan-card.html](http://forum.notebookreview.com/dell-inspiron-dell-studio/648578-need-some-help-finding-drivers-dell-inspiron-6000-broadcom-bcm4322-wlan-card.html)

so at least the card is compatible with the hardware.

However, it may not automatically work in Ubuntu.  Try some googling to see what I mean.

Broadcom does offer a Linux driver for it:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

which you might have to build in a terminal, not sure.

Personally I try to stay away from Broadcom cards and stick with Intel cards for Linux, but I don't think there's an Intel card for the 6000 that is any faster than 802.11g .  This is an old laptop (I've worked on a few of them) and not really worth putting much money into, but you probably know that.

---

### Post by Bobisha on 2012-08-30
Thanks for the help there. I would go with the intel 2915 a/b/g, but I am trying to get something that covers the whole a/b/g/n setup  without  having to get an external router. As far as having to use the terminal to set it up, that is no problem. Granted, I have been using ubuntu for about 10 months now, but its an old windows habit to do most of the software updates that way. The only thing that is holding me back from getting a new laptop is the lack of funds to do so. Besides, I am going to try to get every penny out of this laptop before I have to get a new one (basically that means that when it fries, I get a new one). Again, thanks for the help.

---


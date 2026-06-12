---
title: "Toshiba wireless needs cold reboot"
date: 2010-11-05
forum: Hardware
---

### Post by bobnw on 2010-11-05
Using:
Toshiba A215 series with Ubuntu 10.04 and Vista


If I enter sleep mode sometimes I am not able to reconnect to a wireless network.  The odd thing is that if I restart and switch to Vista I still can not connect.  Vista says the network adapter is not working.  But if I shut down completely and do a cold reboot the connection is back on both operating systems.  We just swithced from cable to DSL wireless modem.   Is there any way this could cause the problem?

The fact that it occurs with both operating systems suggest it  is a hardware problem.   I am  hoping that  an Ubuntu guru will suggest way to confirm this before I replace the wireless card.  

Thanks for being there.

---

### Post by coffeecat on 2010-11-05
Have a look at post #2 from this thread on another forum. It probably explains what is happening. The poster mentions USB dongles but I believe it's true of PCI and mini-PCI cards as well.

[http://www.linuxformat.com/forums/viewtopic.php?t=8974](http://www.linuxformat.com/forums/viewtopic.php?t=8974)

I've not ever experienced this when warm rebooting between Linux and Windows, but perhaps I've been lucky with the wireless devices I've used. Out of interest, do you know what chipset yours is? The output of 'lspci' should tell you if it's an internal device and not a USB stick.

---


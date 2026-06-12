---
title: "DWA-547 card not found by the system."
date: 2008-10-20
forum: General Help
---

### Post by zelekt on 2008-10-20
As the topic says, my shiny new network card isnt found by the system. 

I'm using ndiswrapper and I've got the driver installed, but when I do a lspci the output I get is as following:


&#65533; lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
**01:09.0 Network controller: Atheros Communications, Inc. Unknown device 0003 (rev 01)**
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

As you can see, the network card isnt recognized. 

You guys have any ideas on what I should do?


EDIT: For the record, I have madwifi installed too, but the card is found as ioctl there. Any hints?

Thanks :)
Zelekt

---

### Post by shawnrgr on 2008-10-20
This bug was confirmed on 2007-03-04 and is on the wishlist, you should search launchpad and the forums before purchasing new hardware mate, sorry. but that doesn't mean it can't be fixed with a little elbow grease ;)

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/85455](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/85455)

---

### Post by zelekt on 2008-10-21
Ok.

It's typical, how the only wireless card they had in the shop, is a card that isnt supported :\

---


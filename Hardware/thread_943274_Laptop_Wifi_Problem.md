---
title: "Laptop Wifi Problem"
date: 2008-10-10
forum: Hardware
---

### Post by mike.pms on 2008-10-10
I am making the switch from Vista to Linux. I have Ubuntu running great so much better than windows. But im having a problem getting my laptops wireless to work, Ubuntu seems to have installed the right device but i cant get it to find or connect to a network, i installed the Wifi Radar software but still could find any networks.

My card is a Atheros AR5007. I tryed installing the windows driver which said it had installed and the device was working. But i cant find out how to find a network.

This may just be that i havnt set it up right.

Please help on this matter so i can remove Vista once and for all :)

Thanks.

---

### Post by mike.pms on 2008-10-10
Just an update. I downloaded and installed Atheros Linux driver. It is saying it is installed, i followed a fix in a different post.

Typeing: sudo lspci -v
This tells me Atheros AR242x Wireless Adapter is there. But when trying to run: sudo ifconfig ath0 down i get this:

ath0: ERROR While getting interface flags: No such device

? im confused and stuck... Im trying to give as much info as i can, realy need some help please.

Thanks

---

### Post by Sub101 on 2008-10-10
Does the card appear in iwconfig? It may be that it is under a different name.

---

### Post by mike.pms on 2008-10-10
if i run the command 'iwconfig' i get this:

lo  No Wireless extensions
eth0 No wireless extensions.

---

### Post by mike.pms on 2008-10-10
Can anyone recomend a linux distro that would have support for my wifi card? Its a shame i like Ubuntu, but with out wireless its useless.

---

### Post by mike.pms on 2008-10-10
You can close this Thread now. Mandriva works out of the box :) thanks all.

---

### Post by baizon on 2008-10-10
Hi, i got the same Wifi Card, just disable the property driver (Ubuntu 8.10 Beta) and it will word perfect :-)

---


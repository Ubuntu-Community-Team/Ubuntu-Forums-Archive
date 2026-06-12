---
title: "DOH 0 Dell Inspiron 600m Hell"
date: 2008-12-06
forum: Hardware
---

### Post by yanivmeyer on 2008-12-06
Well this is awesome. I do enjoy the distribution however my Dell Inspiron 600m's wireless does not work. 

Here is what I have so far.

 lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


When I try follow the instructions for the following command, see the resulting message.

 sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

Likewise 
 sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

Since all the threads I can find start with these command in fixing the issue, what next?

I am doing this while having an active internet connection and with the Ubuntu 8.1 CD in the drive that I used to install the OS and still no joy? 

Can anyone help me fix this?

Thanks
Yaniv

---


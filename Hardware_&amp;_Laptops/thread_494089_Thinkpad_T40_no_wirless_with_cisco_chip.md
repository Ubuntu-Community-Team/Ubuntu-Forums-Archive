---
title: "Thinkpad T40: no wirless with cisco chip"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by tp21 on 2007-07-06
hi,
i am having Thinkpad T40, Ubuntu 7.04, and i have a problem with connecting to internet using wireless chip.
by running lspci i know that my internal wireless card is: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b. 
i can not connect to net neither with WPA nor without. and i tried network-manager, and system:administration:network, and manually. nothing worked out, although i can see my network with the network-manager but i can not log in.
what to do?
thankx

---

### Post by tp21 on 2007-07-07
i did some researching on the net.
according to thinkwiki.org the cisco chip is supported in linux with the driver "airo". ([http://thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b](http://thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b))
as far as i understood the best combination would be:
airo-driver version 0.6
Cisco firmware version 5.60.17 and 5.20.17
Linux 2.6.11
the only thing which is different with my labtop is the kernel, as i have 2.6.20
do you think this could be the reason? and is it possible to downdate my kernel to check up?
thanks

---


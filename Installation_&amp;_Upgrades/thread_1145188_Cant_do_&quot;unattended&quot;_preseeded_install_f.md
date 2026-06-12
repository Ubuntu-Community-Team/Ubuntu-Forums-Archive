---
title: "Cant do &quot;unattended&quot; preseeded install for connectionless PC !"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by egon1987 on 2009-05-01
Hi, i digged google, 
this [https://help.ubuntu.com/9.04/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/9.04/installation-guide/i386/appendix-preseed.html)
and this [https://help.ubuntu.com/8.04/installation-guide/sparc/boot-parms.html](https://help.ubuntu.com/8.04/installation-guide/sparc/boot-parms.html)

But i cant find any methods how to make unattended "questionless" install possible, the network cable is disconnected, but a network card is found.

I disabled DHCP, because i dont want it. I dont want PC to go to internet eaven if it could.. i want it to install from CD.

Now "d-i netcfg/dhcp_options select "Do not configure the network at this time"" does not work. It still forces me to enter static IP addresses.

If i type some random "correclt formated" IP-s it tells me that the Gateway cannot be contacted and i cannot continue or preseed this error.

All i want is a clean install from CD without any network support.

Only way to preseed "questionless" install at all without network today is to enable DHCP, rape the PC (pull out wire and screw out Wifi cards) and then set DHCP fail to low (1 sec) and use:
d-i netcfg/disable_dhcp boolean true
d-i netcfg/dhcp_options select "Do not configure the network at this time"

Anyone has any better solutions ?

---


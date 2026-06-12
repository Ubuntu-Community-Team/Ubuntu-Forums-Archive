---
title: "I've lost my printer"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by alastair lewis on 2005-07-29
It's an HP Deskjet 6840 with HPLIP (v0.9.3) 
 
I installed and was able to set-up the network printer without dificulty. I initially lost Wifi contact with my printer when the router changed its IP address from 192.168.0.6 to 192.168.0.3 after the printer was switch off. Changing the URI in CUPs restored the connection. This then happened again so I assigned an IP address to the printer, rather than allowing DHCP to assign one automatically (192.168.0.6). 
 
I cannot connect with linux now (works under windows so the IP addess, subnet mask and default gateway must be OK). 
 
For anyone familiar with HPLIP...
./probe -bnet never worked. 
hp-makeuri 192.168.0.6 picks up the printer and makes the URI for CUPS. 
I can ping 192.168.0.6 sucessfully.
 
Running the toolbox I am told that the printer is powered down or unplugged (this is not the case) 
Trying to setup with CUPs finishes with the error (client-error-not-possible)

Can anyone shed any light on what is going on.

---

### Post by alastair lewis on 2005-07-30
For anyone in the same boat...

1) Don't change the printer IP address, tell the router to give your printer a fixed IP Address.

2) The HOWTO at hpinkjet.sourceforge.net is for debian. Amongst the differences is that sudo /etc/init.d/cups restart translates to sudo /etc/init.d/cupsys restart.

Reassinging the printers IP management to the router and restarting CUPS correctly has fixed everything.

---


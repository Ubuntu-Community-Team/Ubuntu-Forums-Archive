---
title: "lt modem module"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by ilias on 2005-07-28
I tried to build the module for my Agere Winmodem from source but no lack. I found that the module exists as lt_modem in the linux-restricted-modules-2.6.10 package. In terminal I typed modprobe lt_modem and by typing <<lsmod>> the module existed. Using Kppp the modem was found, but no information could be taken out of it. with pppconfig i can not connect to the internet whatever port i assign to the modem.
Any help??

---

### Post by az on 2005-07-28
I hope this helps:

[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

---

### Post by ilias on 2005-07-30
[QUOTE=azz]I hope this helps:

[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)[/QUOTE]

Thanks azz ... I'll try it out. I'll post any results.

---

### Post by ilias on 2005-07-30
[QUOTE=ilias]Thanks azz ... I'll try it out. I'll post any results.[/QUOTE]
 nope... no luck

I inserted lt_serial and lt_modem in /etc/modules, I restarted and no /dev/ttLTM0 node appeared.
 
The dmesg has the following output
---
lt_modem: module licence 'Proprietary' taints kernel.
Loading Agere/Lucent WinModem Controller driver version 8.31
agrserial - No device detected
---
Through kppp modem is only found using "query /dev/ttys0" or something serial. It's either 0 or 1, but anyway i get no ATI results.

I forgot to mention since nothing happens at power up with lt_serial, when I type modprobe lt_serial I get a 'fatal error' message, and a 'no such device' message

---

### Post by az on 2005-07-30
Not all Agere winmodems are lucent based.  Try scanmodem.  It may be useable with the sl-modem drivers.

---


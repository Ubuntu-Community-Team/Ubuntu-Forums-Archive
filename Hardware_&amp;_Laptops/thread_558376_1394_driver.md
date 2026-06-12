---
title: "1394 driver"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by Rodrigo Negrete on 2007-09-23
Hi
I have a toshiba satellite 2455 s306 laptop with a TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link). At least that&#347; what a device manager program shows. I&#7743; running kubuntu feisty 7.04. How can I enable, get driver or whatever is needed to get the device working?
Many thanks

---

### Post by geraldm on 2007-09-24
A module to load is ohci1394.ko for a Toshiba Satelite A100.

check 
[https://help.ubuntu,com/community/Firewire](https://help.ubuntu,com/community/Firewire)
check the log when booting, file /var/log/dmesg OR use the command dmesg

Gerald

---

### Post by Rodrigo Negrete on 2007-09-24
Thanks mate, tonight I'll have some time to check how that works. 
Best regards

---

### Post by Rodrigo Negrete on 2007-09-27
Hi, I've been trying to get the module you suggested but I don't know where to get it. What I really want to do with my firewire is to connect and share internet with other computers. Could anyone help me on that?
Many thanks

---


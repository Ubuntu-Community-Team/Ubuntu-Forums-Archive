---
title: "Wifi card not recognised on boot"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by echinida on 2005-02-15
My buffalo 54g pcmcia card works fine with ndiswrapper but I have to go to computer>system configuration>networking remove and reinsert the card and activate it after each start up. The properties>start on boot box is ticked. boot hangs at configuring network if the card is in until a time out happens. Where do I fix this?

---

### Post by slow'puter on 2005-02-23
I have the same question. 

Anyone?

---

### Post by Spif on 2005-02-26
Press Crtl + C when it checks for netwoks during startup to skip it.

---

### Post by alastair on 2005-02-26
Post some logs of a boot that "hangs" - it might be possible to see what is happening i.e. look in :

/var/log/syslog

---


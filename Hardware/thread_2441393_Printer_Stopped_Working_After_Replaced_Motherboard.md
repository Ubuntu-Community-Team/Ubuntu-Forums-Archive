---
title: "Printer Stopped Working After Replaced Motherboard Battery"
date: 2020-04-23
forum: Hardware
---

### Post by maffwilson on 2020-04-23
Hello, recently my PC would not boot, complaining about the processor not being detected.  After I'd changed the motherboard battery it reset itself and is working fine, only my printer has stopped responding.  

I've tried 
sudo su -c 'journalctl -u cups.service --since="None" --until="2020-04-23 10:49:36"' > troubleshoot-logs.txt
Failed to parse timestamp: None

and the commands on the printer debugging page, they all seemed to be okay apart from 

sudo cat /proc/sys/dev/parport/parport*/autoprobe*

which returned nothing

I suspect that something is wrong with the time the printer uses but I really know nothing about this stuff beyond that vague hunch.

Any help very much appreciated.

Thank you

---

### Post by maffwilson on 2020-04-23
Troubleshoot.txt is at [https://paste.ubuntu.com/p/65gCQsrcZ9/](https://paste.ubuntu.com/p/65gCQsrcZ9/)

---

### Post by maffwilson on 2020-04-23
My mistake: cables: really thought I'd checked them.  Not so much.  OOOps.  Apologies :oops:

---


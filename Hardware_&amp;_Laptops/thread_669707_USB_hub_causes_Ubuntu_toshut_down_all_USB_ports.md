---
title: "USB hub causes Ubuntu toshut down all USB ports"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by vseehua on 2008-01-16
I've just bought a new USB 2.0 high speed hub with intergrated memory card reader. It ran perfectly fine under Windows Xp and Fedora 8. But when i tried to boot my laptop into Ubuntu, the kernel seemed to disable all of my USB ports including the hub and the rest of the unused ports. 

Here I would like to request for help in troubleshooting this problem of mine, thanks.

Here are the outputs i get from lsusb command (hub disconnected after start up, but an external mouse is connected) :
casper@casper-laptop-ubuntu-804:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Laptop: Acer Aspire 5504
Processor: Intel Pentium M 2.00GHz
Memory: 1 Gb DDR2 533
Graphics: Ati X700 mobilty
Chipset: Intel 915PM express

---


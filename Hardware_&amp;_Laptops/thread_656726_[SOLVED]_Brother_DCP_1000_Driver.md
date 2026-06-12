---
title: "[SOLVED] Brother DCP 1000 Driver"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by bwtranch on 2008-01-02
Boy, talk about frustrated. I wrote the how-to on how to install the driver for this printer! I had a problem with the AMD 64 and had to re-install Ubuntu. Now, my own instruction don't work! I did everything to the letter, I think. It could be a hardware problem. the output of lsusb:

jim@jim-desktop:~$ lsusb
Bus 002 Device 004: ID 050d:705c Belkin Components 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04f9:0112 Brother Industries, Ltd 
Bus 001 Device 004: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000  
jim@jim-desktop:~$ 

I am getting the error message "printer 'DCP 1000' may not be connected". But it is. Maybe I don't have the cupswrapper configured right? Any ideas would be appreciated. Thanks.

---

### Post by bwtranch on 2008-01-15
Found the problem. Switched back to the 32-bit machine and it works great.

---


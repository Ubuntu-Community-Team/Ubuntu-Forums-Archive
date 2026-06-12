---
title: "Parallel port problem"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by iraj on 2005-08-14
I'm trying to install an HP Laserjet 6P by going to System->Adminstration->Printing and add a new printer. The problem is that my parallel port does not appear among the ports that I can choose. But I can see USB Printer # 1 up to USB Printer # 16

I have run lsmod and can see that the the parport module is running:
parport                33480  2 parport_pc,lp

How do I get the parallel port configured to get it in the list?

---

### Post by iraj on 2005-08-18
A good friend asked me to check the bios to be sure that the port was enabled. And guess what is was not enabled so the problem was solved by just enabling the port in bios.

---

### Post by razeshkale on 2007-07-05
I do have same problem
I have Ubuntu server 64 bit
and we are uding Donle on this Box enable to get work around Dongle
Anyone has any Idea?
How to check Parallel port is working in Ubuntu?
Cheers

---


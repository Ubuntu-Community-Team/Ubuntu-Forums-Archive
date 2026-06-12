---
title: "SMP problems - Intel Pentium D820"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by aaronb on 2006-01-01
Hi there,

I have been trying to run ubuntu on my PC but have run into constant lockups :( . The install went fine. Updating using the update tool was cool :) . But after about 2 to 4 hours of uptime ubuntu locks up.

I noticed that the default kernel uses one CPU. So I tried the x86_64 for Xeon and then the AMD64 K8 for X2s. Both kernels dont boot. There is some success with booting with apci=off but it locks up after 1/2 hour or so.

Thanks for any help/advice in advance

**Information**
Processor: Intel Pentium D820
Motherboard: (Generic) Reports its self as a MS-7187 (Chip set Intel 945P) 
Graphics: Nvidia 6800GT
memory: Samsung PC4300 
hard drive:2x ST3200822AS (200 GB)
Optical:LITE-ON DVDRW SOHW-1673S R
Optical2:PIONEER DVD RW
Printer: HP 810C 
Network: Intel Pro/100 VE 


Bests regards
Aaronb

---

### Post by aaronb on 2006-01-01
The live cd runs fine. :cool:

---

### Post by aaronb on 2006-01-02
Hi there,

Has any else had problems with SMP ?

Best regards
Aaronb

---

### Post by aaronb on 2006-01-02
Just in case anyone wants to know how to fix the smp problem on intel hardware.

The Dapper Drake flight 2 seems to fix this issue after installing the  Xeon kernel image version 2.6.15.x-x.

Very cool distro. I will report back in if there are any problems.

:razz:

---


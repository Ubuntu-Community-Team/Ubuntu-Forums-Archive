---
title: "[SOLVED] Linux Benchmarking Toolkit"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by altonbr on 2006-12-16
**What is it?**
From what I gather through my quick scanning, LBT is more of a theory behind how to properly benchmark a system.

**Where can I get it?**
I've downloaded the PDF version of [http://tldp.org/HOWTO/Benchmarking-HOWTO.html](http://tldp.org/HOWTO/Benchmarking-HOWTO.html) and will read it later, but is there a specific program I can run to get these results? Or is it as I suspected; It's the combination of several benchmarking programs put together, complied into a need list.

Because I must say, I would prefer this output, versus CPU-Z's:

> **LINUX BENCHMARKING TOOLKIT REPORT FORM**

CPU 
== 
Vendor: Cyrix/IBM 
Model: 6x86L P166+
Core clock: 133 MHz
Motherboard vendor: Elite Computer Systems (ECS)
Mbd. model: P5VX-Be
Mbd. chipset: Intel VX
Bus type: PCI
Bus clock: 33 MHz
Cache total: 256 KB
Cache type/speed: Pipeline burst 6 ns
SMP (number of processors): 1

RAM 
==== 
Total: 32 MB
Type: EDO SIMMs
Speed: 60 ns

Disk 
==== 
Vendor: IBM
Model: IBM-DAQA-33240
Size: 3.2 GB
Interface: EIDE
Driver/Settings: Bus Master DMA mode 2

Video board 
=========== 
Vendor: Generic S3
Model: Trio64-V2
Bus: PCI
Video RAM type: EDO DRAM 
Video RAM total: 2 MB
X server vendor: XFree86
X server version: 3.3
X server chipset choice: S3 accelerated 
Resolution/vert. refresh rate: 1152x864 @ 70 Hz
Color depth: 16 bits

Kernel 
=====
Version: 2.0.29
Swap size: 64 MB

gcc 
=== 
Version: 2.7.2.1
Options: -O2
libc version: 5.4.23 

Test notes 
==========
Very light load. The above tests were run with some of the special 
Cyrix/IBM 6x86 features enabled with the setx86 program: fast ADS, 
fast IORT, Enable DTE, fast LOOP, fast Lin. VidMem.

RESULTS 
======== 
Linux kernel 2.0.0 Compilation Time: 7m12s
Whetstones: 38.169 MWIPS. 
Xbench: 97243 xStones. 
BYTE Unix Benchmarks 4.01 system INDEX: 58.43
BYTEmark integer INDEX: 1.50
BYTEmark memory INDEX: 2.50

Comments
========= 
This is a very stable system with homogeneous performance, ideal 
for home use and/or Linux development. I will report results 
with a 6x86MX processor as soon as I can get my hands on one!


(Sysinfo, the one currently support for Edgy (0.6.1), does not give you this kind of information)

---

### Post by altonbr on 2006-12-16
Oh yeah, and just for a laugh, check out this old website: [http://www.tux.org/bench/html/server.html](http://www.tux.org/bench/html/server.html)

(Pentium 166MHz, 64 MB of 60ns EDO DRAM, 2 EIDE HDs, 3 SCSI HDs, PCI Ethernet network adapter // RedHat 4.2 (2.0.29) // Apache // mySQL // PHP/FI // the GIMP)

---

### Post by altonbr on 2007-07-05
I guess what I was looking for was something like the package 'lshw' or Hardware lister.

Use this command to get a .html report:

```
lshw -html > lshw.html
```

---


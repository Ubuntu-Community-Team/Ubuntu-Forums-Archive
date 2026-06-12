---
title: "PCIe card BAR regions ignored on Server 14.04.1 LTS"
date: 2015-02-16
forum: Hardware
---

### Post by mtbhooger-general on 2015-02-16
Hi all,

On my system, with Ubuntu Server 14.04.1 LTS installed, one  of the PCIe boards in the system (06:00.0) is having it's memory regions  ignored:

  ```
Interrupt: pin A routed to IRQ 10
Region 0: Memory at <ignored> (32-bit, non-prefetchable) [size=512]
Region 2: Memory at <ignored> (32-bit, non-prefetchable) [size=2M]

```  In dmesg:
  ```
me@system:~$ dmesg | grep 06:00.0
[    1.326963] pci 0000:06:00.0: [ad00:0122] type 00 class 0x000000
[    1.326979] pci 0000:06:00.0: reg 0x10: [mem 0xf7400000-0xf74001ff]
[    1.327000] pci 0000:06:00.0: reg 0x18: [mem 0xf7200000-0xf73fffff]

```  When I subsequently try and access the board via it's kernel module, it doesn't work of course.

  If I install Debian 7.5 or 7.8 on the system without changing anything else, everything works fine:

  Debian:
  ```
Interrupt: pin A routed to IRQ 17
Region 0: Memory at f7400000 (32-bit, non-prefetchable) [size=512]
Region 2: Memory at f7200000 (32-bit, non-prefetchable) [size=2M]

me@system:~$ dmesg | grep 06:00.0
[    1.438114] pci 0000:06:00.0: [ad00:0122] type 0 class 0x000000
[    1.438130] pci 0000:06:00.0: reg 10: [mem 0xf7400000-0xf74001ff]
[    1.438151] pci 0000:06:00.0: reg 18: [mem 0xf7200000-0xf73fffff]

```  So, the hardware is essentially fine.  

  Ubuntu kernel:  3.13.0-32-generic
  Debian kernel:  3.2.0-4-amd64/

  What can I do to get this working under Ubuntu Server i.e. make the memory regions not be ignored?

  Many thanks!

---


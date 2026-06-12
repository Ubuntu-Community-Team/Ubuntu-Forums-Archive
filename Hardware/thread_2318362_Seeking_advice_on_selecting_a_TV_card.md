---
title: "Seeking advice on selecting a TV card"
date: 2016-03-25
forum: Hardware
---

### Post by satimis on 2016-03-25
Hi all,

This is my first time to add a TV card to computer for viewing TV

Hardware configuration

1)
Motherboard
ASUSTeK COMPUTER M5A97 LE R2.0
Expansion Slots
1 x PCIe 2.0 x16 (blue)
1 x PCIe 2.0 x16 (x4 mode, black)
2 x PCIe 2.0 x1
2 x PCI 

2)
Display card              
VGA compatible controller
GK208 [GeForce GT 730]
NVIDIA Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz

3)
CPU
&#10219; lscpu```

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            21
Model:                 2
Stepping:              0
CPU MHz:               3500.000
BogoMIPS:              7023.69
Virtualization:        AMD-V
L1d cache:             16K
L1i cache:             64K
L2 cache:              2048K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7

```

4)
RAM
&#10219; free -m```

             total       used       free     shared    buffers     cached
Mem:         32078       2794      29283         21        114        912
-/+ buffers/cache:       1767      30310
Swap:        32666          0      32666

```

Could you please recommend me a TV card?  I have no preset budget.

Thanks in advance.

Regards
satimis

---

### Post by TheFu on 2016-03-25
There are different standard for TV around the world. Need to know your location, which standards are used there before anyone can make any valid suggestions.

For example, DTV in Europe is not compatible with anything in the USA.
There are different standards for cable TV vs broadcast TV too.

In the USA, using ATSC broadcast data, I'd not use a PCI-based card at all. Get a network tuner from Silicon Dust, then you aren't tied to any specific HW inside the PC and any device on the network can use popular protocols, like DLNA, to record, or watch, TV.  Plus, if you use a network-based TV tuner, then you can run the TV recording stuff inside a virtual machine easily and just need a cheap, silent, playback device in the same room with the TV or projector.

Make sense?

If you care about Linux support, and you should, then look at the LinuxTV and/or mythtv websites for possible answers too.

---


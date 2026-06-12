---
title: "Old Ubuntu works, 8.1 does not"
date: 2009-01-28
forum: Hardware
---

### Post by don54321 on 2009-01-28
(accidentally posted same to wrong forum area a couple days ago)
Hello, 

After playing around with Ubuntu on older hardware, I decided to take the plunge and put it on my best PC, a home built AMD5000 X2 machine with a quality DFI Motherboard (Nvidia Chipset) and 2G memory. To my horror 8.1 won't proceed much past the load language screen on the live CD boot. I get a message:

0.272200 Kernel Panic - Not Syncing! Out of memory and no killable processes.

I know older, yet recent Ubuntu variants work fine including Mint 5 (not quite sure which Ubuntu is at this core) but not Mint 6, based upon Ubuntu 8.1. I am working with Ubuntu 8.1 now not a variant trying to get to the root of the problem.

My hardware is:
AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
Mainboard : DFI Inc. NF UltraII-M2 /NF SLiII-M2 /NFII -M2
Bus(es) : ISA PCI PCIe IMB USB FireWire/1394 i2c/SMBus
System BIOS : Phoenix Technologies, LTD 6.00 PG
2GB DDR2
NVIDIA GeForce 6200 LE (128MB DDR3, PCIe 1.00 x16, PS 3.0, VS 3.0)

I would hate to find that this platform is incompatible moving forward with future Ubuntu releases.

Any ideas... thoughts?

Don

---

### Post by Bablefish on 2009-01-28
I came across this before, some versions of Ubuntu has problems with some hardware. That is why most reccomend testing out a Live CD before installing anything.

---

### Post by icanfly0307 on 2009-01-28
Out of memory? You've got 2GBs of RAM and the Kernel says out of memory? Sounds like a bad burn with a memory leak. Did you burn the CD at the lowest speed possible?

---


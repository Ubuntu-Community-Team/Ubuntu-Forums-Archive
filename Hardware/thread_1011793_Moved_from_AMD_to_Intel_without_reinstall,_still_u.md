---
title: "Moved from AMD to Intel without reinstall, still using AMD ata module"
date: 2008-12-15
forum: Hardware
---

### Post by speedsix on 2008-12-15
I've just swapped a socket 754 nForce 2 motherboard with an AMD 64 3000+ cpu to a new Core 2 Duo system, 775 motherboard with the nForce 630i chipset.

Everything seemed to work fine except it wouldn't enable DMA for my drives. I've just noticed that it's still using the pata_amd module which I expect is the problem. How would I force the system to redetect the right modules for the motherboard ata controller (without a reinstall preferably!)



Thanks

EDIT: actually it seems pata_amd is also for intel controllers :|

---


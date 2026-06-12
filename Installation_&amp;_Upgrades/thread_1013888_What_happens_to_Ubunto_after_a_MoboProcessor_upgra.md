---
title: "What happens to Ubunto after a Mobo/Processor upgrade?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by Phillyman on 2008-12-17
I just got done installing Ubuntu....and I am thinking about upgrading my computer. I know Windows XP is going to have a seizure after I replace out these parts. But since Ubuntu does not need activating after changes...how will it handle it?

Also I have Ubuntu installed on a 1TB drive right now, I have the following

18GB ext3 for \
18GB ext3 for \home
4GB swap 

If I wanted to buy a 160GB drive to let Ubuntu use instead....is there any program out there that will let me move and resize the Linux partitions to a new disk?


Oh and this is the upgrade I am looking to perform.

**Current Setup**

&#8226; Intel Pentium® D Processor 820 2.8GHz, 800MHz FSB, Socket 775, 2x1MB Cache, Dual Core
&#8226; Intel BOXD945PSNLK 945P P4/Pentium D/Celeron D 1066FSB LGA775 DDR2 ATX Motherboard w/Audio, Gigabit LAN, Serial ATA
&#8226; Kingston ValueRAM 2GB (4 x 512MB) 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) Dual Channel Kit System Memory Model

**New Setup**

&#8226; Intel Core 2 Quad Q6600 Kentsfield 2.4GHz 2 x 4MB L2 Cache LGA 775 Quad-Core Processor
&#8226; GIGABYTE GA-EP45-DS3L Core 2 Extreme P45 DDR2-1200 A&GbE ATX DES Motherboard
&#8226; CORSAIR DOMINATOR 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory


The new setup will run me $327, minus whatever I can sell the current setup for on Ebay.

---

### Post by Topsiho on 2008-12-17
> **Phillyman said:**
> I just got done installing Ubuntu....and I am thinking about upgrading my computer. I know Windows XP is going to have a seizure after I replace out these parts. But since Ubuntu does not need activating after changes...how will it handle it?

Also I have Ubuntu installed on a 1TB drive right now, I have the following

18GB ext3 for \
18GB ext3 for \home
4GB swap 

If I wanted to buy a 160GB drive to let Ubuntu use instead....is there any program out there that will let me move and resize the Linux partitions to a new disk?


Oh and this is the upgrade I am looking to perform.

I am no expert (by a long shot :)), but I do not think that replacing a mobo and processor will ditch your Ubuntu install (Windows I do not know). During the booting the hardware is recognized and the necessary drivers installed, just like when you switch to another monitor or mouse (I think).

The moving and resizing of the Linux partitions to another drive is something else. Possibly this is possible, using GParted or so, or with dd on the command line. But probably (and if the new mobo/processor does ditch your Ubuntu install) it is wiser to reinstall Ubuntu after the hardware changes. On my not so new and fast computer this takes only 25 minutes, and quite some more time for the updates, and reinstalling the programs that I use.

Probably much less time and fuzz (or is it fuss?) than what you are proposing to do.

Hope your mobo or processor are not so new that they are not yet supported by the present kernel, though....

Topsiho

---


---
title: "Server System for Home Usage (Backup, Developement, Medias)"
date: 2009-09-13
forum: Hardware
---

### Post by Rocketeer on 2009-09-13
Dear community,
after 7 days of searching in different forums and studying text and datasheets I am in the process of finalizing my system. But I need the help of some hardware gurus to be sure with hardware compability.

What I want:
- **Ubuntu Server OS** (bittorrent, dlna/upnp, apache2, mysql)
- media accessability (maybe transcoding as well for PS3)
- **Hardware Raid** (for my big photography archive)
- **Gigabit LAN**
- **SATA II** (4-6 ports) + 1 IDE Port
- **housing for 4-6 3.5" HDs**
- and all this together should be **silent** as it will be in my home office or even beside the TV (so nice and small case - cubic?)
- **power consumption should be minimal when idle**

Now the **biggest question**: Which motherboard? As I am really want to have a fully compatible board for Ubuntu. Target processor is a Intel Core 2 Duo E8400 (or Core 2 Quad) - optionally also Pentium 4 (as I want to upgrade the processor later, if possible). Optionally also graphics on-board.

Rest of my thoughts:

* Processor
- Intel Core 2 Duo E8400 or Core 2 Quad Q8300

* Motherboard
- Ubuntu compatible

* Memory
- Corsair ValueSelect, 1x2GB SO-DIMM, DDR3-1066 (maybe only 1GB)

* Case
- Thermaltake Matrix? Any other suggestions?

* PSU
- Silverstone SST-ST40EF v 1.1 Element Series - 400 Watt 

I know this is a hefty thread, but any help is appreciated.

---

### Post by IcarusR on 2009-09-14
I have a home server with mirrored raid. It has a 120mm fan in the bottom of the case pushing air in & psu fan expells air.
Not dead quiet, but bad.
I use a 3ware two port hardware raid card, not cheap but has been working reliably for 5 years.
Graphics, I would stick with Nvidea at present as most other makes seem to have issues with drivers in 9.04 & 9.10.
The best boards for low wattage & probably quietest are the mini ATX ones, one potential down side is that a lot of stuff is
integrated & they are not very expandable. Probably no good for you if you want 6 hdds.
There is a good selection with specs [[COLOR="Red"]here[/COLOR] ]("http://linitx.com/viewcategory.php?catid=137&pp=137")
6 hdds is going to create heat which means you will need a good air flow through the case, which means noise!!
I found it is a matter of compromise!

All food for thought.

---

### Post by gordintoronto on 2009-09-14
> **Rocketeer said:**
> What I want:
- **Ubuntu Server OS** (bittorrent, dlna/upnp, apache2, mysql)
- media accessability (maybe transcoding as well for PS3)
- **Hardware Raid** (for my big photography archive)
- **Gigabit LAN**
- **SATA II** (4-6 ports) + 1 IDE Port
- **housing for 4-6 3.5" HDs**
- and all this together should be **silent** as it will be in my home office or even beside the TV (so nice and small case - cubic?)
- **power consumption should be minimal when idle**

Now the **biggest question**: Which motherboard?
* Processor
- Intel Core 2 Duo E8400 or Core 2 Quad Q8300

* Motherboard
- Ubuntu compatible

* Memory
- Corsair ValueSelect, 1x2GB SO-DIMM, DDR3-1066 (maybe only 1GB)

* Case
- Thermaltake Matrix? Any other suggestions?

* PSU
- Silverstone SST-ST40EF v 1.1 Element Series - 400 Watt 


You have specified laptop memory for a desktop computer.  Better to pick the motherboard, then the memory.

You want a small case which can hold six hard drives?  I'm happy with my Cooler Master Centurion 534, which could hold six hard drives -- but it's BIG.  It has a fan at the front pushing air in, and another at the back pushing it out, but it makes less noise than the system it replaced.

A 400 watt power supply might be marginal.

Sorry, I can't answer your main question.  You must have a huge number of pictures to need more than a terrabyte for them.

---

### Post by Rocketeer on 2009-09-14
This will be my shopping list (draft) for now:

MC: Intel DQ45CB (seems to work very well with Ubuntu)
CASE: Antec Mini P180
PSU: Silverstone Element 400W v1.1
CPU: Intel Core 2 Duo E8400
RAM: Kingston ValueRAM 2GB, DDR2-800MHz, CL5

---


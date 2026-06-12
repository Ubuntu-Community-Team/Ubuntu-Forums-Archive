---
title: "Change of Hardware[Solved]"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by RicJD on 2007-06-21
Hi Guys

I'm about to change my Motherboard, CPU and ram in my computer.  Everything else will be kept the same (including my trusty nVidia graphics card).  I was wondering if I would need to a complete reinstall of Ubuntu.  I'm currently running Fiesty Fawn and have it set up the way I like it.  If anyone could let me know what I would need to do that would be fantastic.

Here are the specs of my new stuff:

Abit AB9 QuadGT iP965, S775, PCI-E
Intel Core 2 Duo E6600, Socket 775
2GB (2x1GB) CorsairTwinX XMS2, DDR2

Thanks in advance

Rick

---

### Post by ukripper on 2007-06-21
> **RicJD said:**
> Hi Guys

I'm about to change my Motherboard, CPU and ram in my computer.  Everything else will be kept the same (including my trusty nVidia graphics card).  I was wondering if I would need to a complete reinstall of Ubuntu.  I'm currently running Fiesty Fawn and have it set up the way I like it.  If anyone could let me know what I would need to do that would be fantastic.

Here are the specs of my new stuff:

Abit AB9 QuadGT iP965, S775, PCI-E
Intel Core 2 Duo E6600, Socket 775
2GB (2x1GB) CorsairTwinX XMS2, DDR2

Thanks in advance

Rick

You need to do complete reinstall of ubuntu to let your OS talk to new hardware and install correct drivers for each. Backup your current data and do a reinstall and then restore your data onto new filesystem. if you have /home seprated from filesystem then you don't need to restore but i would still keep the backup.

---

### Post by RicJD on 2007-06-21
Ok cool, thats what i thought.  I have my /home dir on a seperate partition and back up regaulry so we're off to reinstall.  Thanks ukripper

---

### Post by ukripper on 2007-06-21
> **RicJD said:**
> Ok cool, thats what i thought.  I have my /home dir on a seperate partition and back up regaulry so we're off to reinstall.  Thanks ukripper

No problem mate, let us know how it goes with you.

---

### Post by RicJD on 2007-06-27
Hi ukripper

it all went ok.  I have to load in some extra modules for the jmicron sata to ide chipset otherwise it will only boot ever 20 times or something.  also i had to install 64bit to get ubuntu to see all my memory.  and then stupidly last night, after everything was up and running for a few days i went to repartition my external harddrive using fdisk and picked the wrong harddrive (i got my internal).  so a full reinstall (home dir and all) is needed anyway :(  but at least i know i can get everything working easily

---


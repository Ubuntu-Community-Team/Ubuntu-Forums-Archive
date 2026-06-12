---
title: "CD drive"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by ender42 on 2007-07-08
My CD drive is now no longer recognizing CDs after boot (Dapper LTS).

I know that it's not broken because I can boot off the Warty liveCD (which I have to do if I want my USB hardware supported, since LTS doesn't support my USB anymore).

I've tried checking out mount, and fdisk. 

Not sure what I'm looking for in: lshw - and lsusb isn't found/installed anymore??

       *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@00:02.5
             version: 01
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=SIS_IDE irq=10

---


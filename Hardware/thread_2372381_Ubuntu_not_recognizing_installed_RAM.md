---
title: "Ubuntu not recognizing installed RAM"
date: 2017-09-24
forum: Hardware
---

### Post by ascii27 on 2017-09-24
I have an ASUS Chromebox, M004U. I installed Ubuntu 16.04 LTS, no ChromeOS running.

I installed 8GB of RAM, but it looks like it's only seeing 2GB.

 It came installed with 2GB of RAM. I upgraded it to 8GB RAM by installing this: **[SIZE=2]Crucial 8GB Kit (4GBx2) DDR3/DDR3L 1600 MT/s (PC3-12800) SODIMM 1.35V/1.5V 204-Pin Memory for Mac - CT2K4G3S160BM[/SIZE]**


When I run **free -m**, it says:
```
      total        used        free      shared  buff/cache   available
Mem:        **1988 **        833         640         158         513         816
Swap:        2036         888        1148
```

When I run **sudo lshw -class memory**, it says:


```
  *-firmware              
       description: BIOS
       vendor: coreboot
       physical id: 0
       version: MrChromebox
       date: 07/14/2017
       size: 1MiB
       **capacity: 8128KiB**
       capabilities: pci pcmcia upgrade bootselect acpi
  *-memory
       description: System Memory
       physical id: 5
       slot: System board or motherboard
       **size: 8GiB**
     *-bank:0
          description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          vendor: Unknown (0)
          physical id: 0
          serial: None
          slot: Channel-0-DIMM-0
          size: 4GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
     *-bank:1
          description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          vendor: Unknown (0)
          physical id: 1
          serial: None
          slot: Channel-1-DIMM-0
          size: 4GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)

```
which is what I expected.

So what gives? How do I get the system to see all of the RAM? What am I doing wrong?

Thanks

---

### Post by ascii27 on 2017-09-24
Nevermind. I think I had the wrong firmware. I reinstalled it and now it shows 8GB.

All hail Mr. Chromebox!!!

---

### Post by ascii27 on 2017-09-27
okay, so turns out it's not solved after all.

when I boot cold (ie push the on button on the box), it shows 2GB RAM.
when I reboot, it shows full 8GB.

What gives?

Help please.

Thanks so much

---


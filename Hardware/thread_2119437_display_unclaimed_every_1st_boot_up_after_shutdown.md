---
title: "display unclaimed every 1st boot up after shutdown"
date: 2013-02-23
forum: Hardware
---

### Post by walterddr on 2013-02-23
Hi, I have got the strangest problem lately.
Every time I shutdown the computer and power up, the display solution goes to 800x600 and lshw -c display give me display unclaimed.

I reboot immediately without doing anything, the next boot will config display properly. 

after reboot, lshw -c video gives, 
  *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8600M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128)

Ubuntu version: 12.04 LTS.

Any ideas?

---


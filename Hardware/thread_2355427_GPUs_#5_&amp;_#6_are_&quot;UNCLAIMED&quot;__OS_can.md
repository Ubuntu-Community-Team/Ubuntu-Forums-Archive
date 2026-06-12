---
title: "GPUs #5 &amp; #6 are &quot;UNCLAIMED&quot;?  OS can see them, but can't use them?"
date: 2017-03-12
forum: Hardware
---

### Post by groovy1962 on 2017-03-12
Greetings.

I have 6 GPUs, all NVIDIA 1070s attached to a ASUS Z270A motherboard. (They are using risers.) In building the systems I added GPUs one at a time until I got to four and then decided to add the last two.

The OS Sees all the GPUs but two are "unclaimed".  What does this mean?

I'm running stock Ubuntu 16.04 Server, with NVIDIA CUDA 8.0 SDK installed. (The SDK works and I'm able to run my workload against the four GPUS but to my software the remaining 2 don't seem to exist.)

Here's some diagnostic output:

```
$ sudo lshw -C video
  *-display
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:130 memory:de000000-deffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:131 memory:dc000000-dcffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:d000(size=128) memory:dd000000-dd07ffff
  *-display
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:132 memory:da000000-daffffff memory:60000000-6fffffff memory:70000000-71ffffff ioport:c000(size=128) memory:db000000-db07ffff
  *-display
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:133 memory:d8000000-d8ffffff memory:c0000000-cfffffff memory:b8000000-b9ffffff ioport:b000(size=128) memory:d9000000-d907ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:d6000000-d6ffffff ioport:a000(size=128) memory:d7000000-d707ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:d4000000-d4ffffff ioport:9000(size=128) memory:d5000000-d507ffff


lspci shows them all, though:
$ lspci | grep VGA
02:00.0 VGA compatible controller: NVIDIA Corporation Device 1b81 (rev a1)
04:00.0 VGA compatible controller: NVIDIA Corporation Device 1b81 (rev a1)
05:00.0 VGA compatible controller: NVIDIA Corporation Device 1b81 (rev a1)
06:00.0 VGA compatible controller: NVIDIA Corporation Device 1b81 (rev a1)
08:00.0 VGA compatible controller: NVIDIA Corporation Device 1b81 (rev a1)
09:00.0 VGA compatible controller: NVIDIA Corporation Device 1b81 (rev a1)
```

---

### Post by groovy1962 on 2017-03-12
PS- I've swapped around risers a bit and stuff like that.  PSU is 1600 watts, and because all of them are seen by the OS and plugged in all the GPUS were running-- putting full load on the 4 I can the system is pulling only 432 watts at the wall-- so it's not a PSU problem.  When there have been hardware problems in the past, the OS hasn't seen the GPU at all. 

Here it looks like the OS can see the GPU but something isn't claiming it???

---

### Post by DuckHook on 2017-03-12
*Thread moved to **Hardware** as the more appropriate forum.*

---


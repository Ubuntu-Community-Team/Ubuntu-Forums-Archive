---
title: "Strange NVIDIA Driver problem...urgent"
date: 2011-09-25
forum: Hardware
---

### Post by superduperlinuxperson on 2011-09-25
HI all people,
i am running ubuntu 10.04 (works great), but their is just one problem, i am not able to install the nVidia driver from their page, nor does it show up in hardware drivers. when i run $ sudo lshw -C video it tells me that i am using Intel corporation gm965/gl960 graphics chip. but, when i run $ sudo apt-get --purge remove nvidia* and blacklist nouveau and i reboot, it says it cant find the nvidia driver. when i attempt to install it, it says the GPU is not compatible.
Outputs:
$ sudo lshw -C video:

*-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:fea00000-feafffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size= 8 )
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febfffff
the reason why i want the latest driver is because i want to run Urban Terror at more than 9 fps :) , which sucks.
Thanks in advance:popcorn::p;);):D:)

---

### Post by .... on 2011-09-25
You probably need to delete your /etc/X11/xorg.conf file.

> i want to run Urban Terror at more than 9 fps
With an older Intel chip? Good luck with that...

---

### Post by papibe on 2011-09-25
I'm afraid you can't use the Nvidia proprietary driver over a non Nvidia card.

Regards.

---


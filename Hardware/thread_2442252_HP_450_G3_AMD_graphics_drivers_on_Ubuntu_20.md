---
title: "HP 450 G3 AMD graphics drivers on Ubuntu 20"
date: 2020-05-01
forum: Hardware
---

### Post by petermunyalo on 2020-05-01
how do i install AMD graphics drivers on Ubuntu 20, that i installed on my HP 450 G3? 

muna@muna-PC:~$ sudo lshw -c display
[sudo] password for muna: 
  *-display                 
       description: VGA compatible controller
       product: Skylake GT2 [HD Graphics 520]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:e1000000-e1ffffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff
  *-display
       description: Display controller
       product: Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445 / 530/535 / 620/625 Mobile]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 83
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:131 memory:d0000000-dfffffff memory:e0000000-e01fffff ioport:3000(size=256) memory:e2000000-e203ffff memory:e2040000-e205ffff

---

### Post by Autodave on 2020-05-01
You probably will not need to install any additional drivers: they should already be present in the installation software.  If in doubt, create your install medium (DVD or USB) and do a trial run and see if it works.

---

### Post by CelticWarrior on 2020-05-01
Indeed as above.

Both Intel and AMD drivers are already installed, as expected.

---

### Post by Yellow Pasque on 2020-05-01
> configuration: driver=amdgpu
^The correct driver is already installed and in use.

But since this a hybrid graphics laptop, you have to use DRI_PRIME=1 if you want to run something on the discrete AMD GPU rather than the integrated Intel GPU. For example:
```
glxinfo -B      #Should show Intel GPU details
DRI_PRIME=1 glxinfo -B    #Should show AMD GPU details
```

---


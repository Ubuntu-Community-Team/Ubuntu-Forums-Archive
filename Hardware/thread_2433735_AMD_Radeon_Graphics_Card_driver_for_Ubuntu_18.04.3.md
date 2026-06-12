---
title: "AMD Radeon Graphics Card driver for Ubuntu 18.04.3"
date: 2019-12-24
forum: Hardware
---

### Post by parag-93 on 2019-12-24
I am new ubuntu user and using ubuntu 18.04.3. I wonder if there is any driver is installed for my dedicated graphics card AMD radeon HD 8670M by default in ubuntu 18.04.3. If not how can I get one which will support the card on the mentioned version of ubuntu.
The command $ lspci -nn | grep -E 'VGA|Display' returned the following:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430 / Radeon 520 Mobile] [1002:6660]

```

---

### Post by Bashing-om on 2019-12-24
parag-93; Hello

Let's look for a digital device:
```

lspci -k | grep -iEA5 'vga|3d'

```

And to see if a driver is loaded:
```

sudo lshw -C display

```

[INDENT][INDENT]on the way to help
[/INDENT][/INDENT]

---

### Post by parag-93 on 2019-12-25
These are the outputs:
```
parag@parag-PC:~$ lspci -k | grep -iEA5 'vga|3d'
    00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Hewlett-Packard Company 3rd Gen Core processor Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
    Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family USB xHCI Host Controller
```
And,
```
parag@parag-PC:~$ sudo lshw -C display
[sudo] password for parag: 
  *-display                 
       description: Display controller
       product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430 / Radeon 520 Mobile]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:30 memory:a0000000-afffffff memory:c2000000-c203ffff ioport:4000(size=256) memory:c2040000-c205ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:c3000000-c33fffff memory:b0000000-bfffffff ioport:5000(size=64) memory:c0000-dffff
```

---

### Post by CatKiller on 2019-12-25
The drivers for both your Intel and AMD devices are already included with nothing extra that needs to be installed. The AMD side for older devices defaults to the older "radeon" driver, but there is a newer "amdgpu" driver with newer features like vulkan support. You can read a bit more about the differences, and how to enable amdgpu, [here](https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-linux50&num=1).

---

### Post by parag-93 on 2019-12-25
> **CatKiller said:**
> The drivers for both your Intel and AMD devices are already included with nothing extra that needs to be installed. The AMD side for older devices defaults to the older "radeon" driver, but there is a newer "amdgpu" driver with newer features like vulkan support. You can read a bit more about the differences, and how to enable amdgpu, [here]("https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-linux50&num=1").
I tried to install both *amdgpu-pro-18.20-673703-ubuntu-18.04.tar.xz* and *amdgpu-pro-19.10-785425-ubuntu-18.04.tar.xz.* But in both cases, the PC failed to boot after installation. Is there any supported AMD gpu for my model?

---

### Post by CatKiller on 2019-12-25
> **parag-93 said:**
> I tried to install both *amdgpu-pro-18.20-673703-ubuntu-18.04.tar.xz* and *amdgpu-pro-19.10-785425-ubuntu-18.04.tar.xz.* 

> **CatKiller said:**
> The drivers for both your Intel and AMD devices are already included with nothing extra that needs to be installed.

...

---


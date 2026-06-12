---
title: "How to see live frequency of an AMD GPU using the &quot;Radeon&quot; driver on Xenial (16.04) ?"
date: 2016-07-22
forum: Hardware
---

### Post by Swiss_Knight on 2016-07-22
Hi,
How could I know the **actual running frequency** of my AMD gpu on Ubuntu 16.04 ? (_not_ the vendor stock freq)
I can't find any information about this.


```
$ uname -r
4.4.0-28-generic

$ lspci -nn | grep VGA
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cypress PRO [Radeon HD 5850] [1002:6899]


$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Cypress PRO [Radeon HD 5850]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:d0000000-dfffffff memory:fe9e0000-fe9fffff ioport:e000(size=256) memory:fe9c0000-fe9dffff


$ sudo dmidecode -t 2
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: M4A89TD PRO USB3
    Version: Rev 1.xx

```

Here is the 'glxinfo' result : [http://pastebin.com/raw/JXmYEqMP](http://pastebin.com/raw/JXmYEqMP)
And the 'modinfo radeon' command : [http://pastebin.com/raw/4yjcjQkc](http://pastebin.com/raw/4yjcjQkc)

Thanks a LOT ! :)
I feel my GPU isn't running at full speed with some softwares.

---

### Post by snkmoorthy on 2016-10-05
Please check here  - [https://gitlab.com/Espionage724/Linux/blob/master/Devices/AMD-GPU.txt](https://gitlab.com/Espionage724/Linux/blob/master/Devices/AMD-GPU.txt)

---


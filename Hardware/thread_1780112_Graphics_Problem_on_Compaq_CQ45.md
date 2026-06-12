---
title: "Graphics Problem on Compaq CQ45"
date: 2011-06-11
forum: Hardware
---

### Post by markandey on 2011-06-11
Hi Guys,
I have Ubuntu 11.04 on my machine (Compaq CQ45), it has Intel Graphics card. I was able to activate all compiz animation on 10.04 but they are not working on 11.04

I installed GNOME3 on top of the Unity but problem is not fixed instead i am not able to get any window when logging in Unity.

Here is the output of ```
sudo lshw -C display; lsb_release -a; uname -a > out.txt
```
```

  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:90000000-903fffff memory:80000000-8fffffff ioport:60f0(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:95400000-954fffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty
Linux markandey-lappy 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
markandey@markandey-lappy:~$ sudo lshw -C display; lsb_release -a; uname -a > out.txt
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:90000000-903fffff memory:80000000-8fffffff ioport:60f0(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:95400000-954fffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

```


Please help me. 

Thanks in advance

---

### Post by Yellow Pasque on 2011-06-11
Post your /var/log/Xorg.0.log (use [ code ][ /code ] tags).

---


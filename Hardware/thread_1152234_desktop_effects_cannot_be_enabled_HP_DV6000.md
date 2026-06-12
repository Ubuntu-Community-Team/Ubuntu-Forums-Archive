---
title: "desktop effects cannot be enabled HP DV6000"
date: 2009-05-07
forum: Hardware
---

### Post by pvssanjeev on 2009-05-07
I am using HP DV6000 laptop. I have got NVIDIA GeForce GO 7400 card installed.

I just downloaded and installed UBUNTU 9.04.

i was amazed by the kool graphics and the 3D effects. now i am not able to enable any of that.

can you please let me know why?
Is it a problem with the drivers or something is wrong with my laptop.

VISTA was working fine. but UBUNTU is not fine.

i put lshw-

          *-display UNCLAIMED
                description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0

Thanks,
Sanjeev.

---

### Post by rainwalker on 2009-05-08
Just for the heck of it, try
```
SKIP_CHECKS=yes compiz
``` in a terminal and see what happens

---


---
title: "Unable to enable visual effects on Ubuntu10.04LTS"
date: 2012-09-29
forum: Hardware
---

### Post by COmetLord on 2012-09-29
Hi,all

I am not able to activate the normal or extra visual effect for my thinkpad e420 with intel gpu. I am using ubuntu 10.04.4, with 2.6.38-16 kernel.

the output of "lshw -C video":
  *-display               
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5000(size=64)

any help would be appreciated. Thanks

---

### Post by COmetLord on 2012-09-29
Previous before I install some third party intel graphic driver and upgrade linux kernel to 2.6.38-16.67(I was using the most updated kernel under ubuntu 10.04 which is 2.6.32-43.97), I was not even able to set the display to the right resolution(1366x768) and the monitor setting said the display is "unknown monitor".

---


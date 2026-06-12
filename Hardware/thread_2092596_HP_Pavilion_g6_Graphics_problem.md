---
title: "HP Pavilion g6 Graphics problem"
date: 2012-12-08
forum: Hardware
---

### Post by gotharious on 2012-12-08
Hello everyone,

I'm having trouble with my laptop, at first the screen went off while booting, so I started using ubuntu with nomodeset option.

but now I would like to start using it normally, so any idea how can I get it to work properly?

lshw

```
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:90000000-903fffff memory:80000000-8fffffff ioport:4000(size=64)

```
lspci | grep VGA


```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```Thanks in advance

---


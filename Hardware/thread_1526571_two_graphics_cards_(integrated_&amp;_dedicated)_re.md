---
title: "two graphics cards (integrated &amp; dedicated) results in flickering external screen"
date: 2010-07-08
forum: Hardware
---

### Post by JeroenJ on 2010-07-08
Hey all,

So far I have searched for a solution for my flickering external screen, but without any results... My laptop is a HP dv3 2350ed with two graphics cards, an integrated one on the i5 processor (intel GMA) and an ATI HD4500 series for better 3D acceleration. Its a good laptop, but only with a 13.3'' screen, so for work I prefer an external monitor (I'm using the Brilliance 220SW from Phillips). By default the intel drivers are installed and this is also the card I'd like to use since it consumes less power then the ATI when running on the battery.

So, the problem: When I plug in the external monitor using the VGA connection I get signal, but it seems that the (horizontal) refresh rate isn't correct. I think that it is not due to the settings, I tried possible settings using xrandr without any improvement. I think the problem is the following. Since the laptop has two graphics cards, and linux is not used to this, the two are both trying to use the VGA output. Here is what 'lshw -C video' gives me:


```
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: M93 [Mobility Radeon HD 4500 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff(prefetchable) ioport:7000(size=256) memory:ea400000-ea40ffff memory:ea420000-ea43ffff(prefetchable)
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:37 memory:e0000000-e03fffff memory:d0000000-dfffffff(prefetchable) ioport:8050(size=8)
```


Can somebody clarify the info above? Or does somebody has a similar problem?

The laptop also has van DVI port, but I don't have a cable :S


Thanks!



PS I'm using 10.04 and use autodetect for the hardware, so I don't have a xorg.conf file

---


---
title: "PCMCIA core module not loading in updated kernel"
date: 2006-05-09
forum: Hardware &amp; Laptops
---

### Post by geek.de.nz on 2006-05-09
My pcmcia_core module does not load/exist in my newly compiled kernel. How do I make sure it gets installed (kernel config)?

I did enable the following and thought that should work:
CONFIG_HOTPLUG, CONFIG_PCMCIA, CONFIG_CARDBUS, CONFIG_ISA
in my /usr/src/linux/.config file, but the module still does not get installed.

I always get (when trying to load pcmcia_core):
 	Code:
 	[LEFT]# modprobe pcmcia_core
FATAL: Module pcmcia_core not found.[/LEFT]
 
 
Any ideas? I want to get my wireless card working, which runs fine with the standard kernel in my distribution (Kubuntu 5.10, kernel 2.6.12-10-686). But I also want hibernate (suspend2) to work, thus I need a self-compiled kernel. Any ideas?

Here my lshw ouput for the device I'm trying to get to work. Funny that it is still there when the pcmcia_core module isn't loaded:
```

     *-network UNCLAIMED
          description: Network controller
          product: Ralink RT2500 802.11 Cardbus Reference Card
          vendor: RaLink
          physical id: 1
          bus info: pci@03:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          resources: iomemory:f4000000-f4001fff irq:11

```

---


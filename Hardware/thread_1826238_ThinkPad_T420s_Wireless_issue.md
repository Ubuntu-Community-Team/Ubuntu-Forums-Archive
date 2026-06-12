---
title: "ThinkPad T420s Wireless issue"
date: 2011-08-16
forum: Hardware
---

### Post by uganaga on 2011-08-16
Hi all,
I've just installed Ubuntu 10.04 LTS 64 bit on my Thinkpad T420s and the wireless does not work. 
How can I fix the problem?
Thank you very much!

---

### Post by uganaga on 2011-08-16
I've checked for device recognition and this is what I get. Does it mean that there is no driver loaded? What could I do?

sudo lshw -C network


  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:d1600000-d161ffff memory:d162b000-d162bfff ioport:4080(size=32)

  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d1500000-d1501fff

---


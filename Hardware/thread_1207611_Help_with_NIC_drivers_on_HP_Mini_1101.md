---
title: "Help with NIC drivers on HP Mini 1101"
date: 2009-07-08
forum: Hardware
---

### Post by farley2k on 2009-07-08
We just bought a couple for work and I would like to get Ubuntu 9.04 working on it (came with XP).  I used a USB drive to install the netbook remix and everything is great *except* the NIC doesn't work.  I left XP on the machine and when I boot to it everything is good so I can rule out hardware issues.  So what do I need to do to get the NIC working?

Someone in another thread suggested posting the reults of "sudo lshw -C network" so I will post them below.  It seems from reading it that the physicaly ethernet card is found but that is as much as I can tell.

Any help would be appreciated

Thanks,
Farley


> *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:25:56:7e:2a:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=198.134.138.95 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:96:eb:56:e7:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by kulstad on 2009-09-04
I am having the same problem. Any help would be appreciated.

---

### Post by farley2k on 2009-09-04
Since you are the first post since the original in July I am not overly confident!  :)

At least wireless works on mine so I can use it but it would be faster to be wired.

---

### Post by psyjoniz on 2009-09-15
^^ bump/subscribe (i am having the same issue :)

---


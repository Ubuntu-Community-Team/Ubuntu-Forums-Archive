---
title: "Network adapters is not working after upgrade to 13.10"
date: 2014-10-10
forum: Hardware
---

### Post by amiralex32 on 2014-10-10
deear all i have just upgrade from ubuntu 12.10 to 13.10 after that i lost all my connections using network adapters wirless or NIC
so i run this command
sudo lshw -C network -numeric
and the result is 

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN [14E4:4311]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX [14E4:170C]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:ef9fe000-ef9fffff
what can i do to get them back working well thx for help

---

### Post by yancek on 2014-10-10
> i have just upgrade from ubuntu 12.10 to 13.10

Neither is currently supported so I'm not sure why you would want 13.10.  If you actually upgraded to 13.10 you might as well continue to 14.04 which is supported and you may find your problem resolved.

---


---
title: "Network Connectsion Gone After Upgrade"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by kecker on 2009-07-31
Had a pre-existing 9.04 Ubuntu install running, and everything was running fine.  I normally connected via a wireless connection with my home network but also could connect via a wired connection.  Hadn't run Update Manager for 3 days so I did just now and had it install everything.  I requested a restart so I restarted.

Once it came up I got no network connections, wireless or wired.  Near as I can tell it's not even recognizing any devices.

lspci -v | grep Ethernet 
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:40:3e:37:63:36
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7840 (7.8 KB)  TX bytes:7840 (7.8 KB)

Not sure where to start....

---

### Post by kecker on 2009-07-31
nothing?

---

### Post by laburnum on 2009-07-31
Same problem here.    Ran update manager last night, today i can't see the windows machine on my network.  

It will see the workgroup, but it wont mount the drive.

---

### Post by kecker on 2009-08-11
I fell back to the 2.6.8.28-13 kernel and it works just fine.  Any idea why?

---


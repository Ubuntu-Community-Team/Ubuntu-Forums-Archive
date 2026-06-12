---
title: "Atheros ATL1E driver playing up?"
date: 2011-01-23
forum: Hardware
---

### Post by Ubunterrific on 2011-01-23
Hi ubuntuforums! :) 
 
 This is the first problem i've had that i couldn't figure out how to solve, so i hope someone can help.
 
 About a week ago, since returning to university, i noticed that  everytime i powered off my Asus X5EA laptop, network-manager would tell  me that my ethernet connection was eth1 then eth2 etc. Basically,  everytime i shutdown/restarted, a new "eth*" was being created that  superceded the older ones. 
 
 The university employs MAC address filtering, so everytime a new "eth*"  is made, i have to register again that this device is mine. That means  that everytime i shutdown, the MAC address changes and i have to in  effect register a 'new' device. This has been going on for a while now, so  i'm sure to have a big list of devices against my name now lol
 
 (Unfortunately, the wireless isn't set up yet at this part of campus, so a wired connection is essential to me.)
 The device in question is:
 
 ```
02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
``` Relevant output from "sudo lshw -C Network" shows:
 
 ```
  *-network               
        description: Ethernet interface
        product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
        vendor: Atheros Communications
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: eth6
        version: b0
        serial: 00:00:63:db:92:f7
        size: 100MB/s
        capacity: 1GB/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=ATL1E  driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=131.231.254.229  latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
        resources: irq:42 memory:feac0000-feafffff ioport:e800(size=128)
``` 

Using "lsmod | grep atl1e" i see that the driver is loaded but it does  have a "0" in the "used by" column?  I'm using Ubuntu 10.10 and kernel  2.6.35.25 generic. Downgrading back to 2.6.35.24 didn't help :(  
 
 I think this problem is hardware related. Are there any solutions e.g.  putting something in /etc/network/interfaces or would you compile a new  atl1e driver and replace the existing one?

---

### Post by Ubunterrific on 2011-01-23
I'd also like to add that i had no problems whatsoever using a wired and a wireless connection back home; it's only since coming back to university that the MAC address insists on changing everytime i switch off :(

---


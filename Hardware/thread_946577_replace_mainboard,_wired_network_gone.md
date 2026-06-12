---
title: "replace mainboard, wired network gone"
date: 2008-10-13
forum: Hardware
---

### Post by tesna on 2008-10-13
Hi guys, 

Recently I have little problem with my Thinkpad T61. I bring it to service center and to fix it they need replace my mainboard with new one. 

Everything went fine as before, nvidia graphics, sounds, wireless lan, bluetooth, etc but ubuntu hardy does not detect the wired network card. Maybe it has something to do with new mac address? How do I reconfigure the network card in ubuntu hardy 64 bit? The wired network card detected fine in vista x64. 

Regards, 


Tesna

---

### Post by cariboo on 2008-10-13
What chipset is your wired nic using? In a terminal type:

```
sudo lshw -C network
```

Then post your output in your next post.

Jim

---

### Post by tesna on 2008-10-15
sorry for the late reply. 

The chipset is an intel gigabit. The output of lshw -C network shows the network card is disabled. 

Currently I dont have access to wireless network so I saved it on a text file. However the text file kinda got funny layout if opened in window's notepad. 

```

sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 03
       serial: 00:21:86:5c:3c:36
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.2.0 duplex=full firmware=0.3-0 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:29:a9:29
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11abgn


```

---

### Post by cariboo on 2008-10-15
You may need to install a newer kernel version to get proper support for your wired nic. THere was a problem with the driver, but it has been repaired in kernel version 2.6.27. I  would wait until Intrepid Ibex comes out on the 30th of October, it should be supported out of the box.

Jim

---

### Post by tesna on 2008-10-15
thanks for the reply cariboo907, it turns out I just need to update my wicd configuration to eth1 from eth0 and I did not try to manually configure the wired network. Now my wired is working perfectly. 

PS: I'm using custom compiled 26.25.10 kernel on hardy, maybe that's why I dont have problem the driver. I'll update it to intrepid anyway when it's officially out :)

---


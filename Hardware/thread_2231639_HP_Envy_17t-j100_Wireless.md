---
title: "HP Envy 17t-j100 Wireless"
date: 2014-06-26
forum: Hardware
---

### Post by kd5tmu on 2014-06-26
I've done my best to search this issue on here, with no avail.  I'm hoping I haven't overlooked something, lest I be embarassed by a smart alec who just posts a link to another thread.  I have the aforementioned computer, and I've just installed Ubuntu 12.04.4 LTS.  The Live Disk had the wifi working, so I went ahead with the install.  Now, it doesn't work, the wifi switch in the f12 button is non-responsive.  I ran ```
sudo lshw -C network
``` and got the following:
```
  *-network UNCLAIMED     
       description: Network controller
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d3600000-d3601fff

```

I'm wondering how to get this wireless working. Any help is appreciated.

---

### Post by Bucky Ball on 2014-06-26
Your output from 'sudo lshw -C network'. That is all you got? There is nothing missing down the bottom of the output?

I'm no smart alec, but try chilli555's advice here:

[http://ubuntuforums.org/showthread.php?t=2200069&p=12902872&viewfull=1#post12902872](http://ubuntuforums.org/showthread.php?t=2200069&p=12902872&viewfull=1#post12902872)

They're no smart alec either, but they certainly across most things 'wireless'. You are going to need to be connected to an ethernet cable and be online for the above fix to work. Good luck.

PS: This is getting warmer ...

[http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi)

Looks like that's the driver you're after.

---

### Post by kd5tmu on 2014-06-26
There was information on the wired network.  Immediately under that:

```

 *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0f:00.0
       logical name: eth0
       version: 0c
       serial: a0:1d:48:f9:9d:cc
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:d3500000-d3500fff memory:d3400000-d3403fff

```

I'll give the above information a look-see and hopefully it helps.  Thanks for your reply!

---

### Post by Bucky Ball on 2014-06-27
If you do an update you could also check under 'Additional Drivers' and see if it is there ready and waiting.

---


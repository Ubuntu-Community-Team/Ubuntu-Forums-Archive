---
title: "How to enable my bcm43 on inspiron 1545"
date: 2010-01-17
forum: Hardware
---

### Post by eldouchebago on 2010-01-17
Ok after searching all morning and several re-install attempts, I am beaten!

here's what I get when I run sudo lshw -C network

 *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:1a:07:6f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.0.11 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)



This is what I have tried:

1. go into BIOS and make sure wireless is enabled
2. downloaded several drivers and used windows drivers
3. a bunch of other random solutions purported to work.
4. a fresh re install after every attempt (to ensure I wasn't doing something I didn't understand with some of the changes to /etc and all that)

the closest I could come to the same problem in a related thread was
[http://ubuntuforums.org/archive/index.php/t-1252464.html](http://ubuntuforums.org/archive/index.php/t-1252464.html)

Notice his shows the logical name = eth1 (which mine does not)

I am not sure if there is some other hardware way to enable the device.....I am at a total loss....HELP!

thanks

---


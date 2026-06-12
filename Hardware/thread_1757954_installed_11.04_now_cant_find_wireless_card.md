---
title: "installed 11.04 now cant find wireless card"
date: 2011-05-14
forum: Hardware
---

### Post by ogurs29 on 2011-05-14
dell latitude D620 uses b34 wireless card.  the wireless card worked fine today until i switched to ubuntu.  now it is undetectable. here is what i got after doing all the tests.
State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:15:C5:41:1F:35

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


kevin@kevin-Latitude-D620:~$ sudo lshw -C network
[sudo] password for kevin: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:ecffc000-ecffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:41:1f:35
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.19 ip=192.168.1.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:ecef0000-ecefffff
kevin@kevin-Latitude-D620:~$  sudo apt-get install lshw 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lshw is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kevin@kevin-Latitude-D620:~$

---

### Post by abhaic on 2011-06-15
I have same problem with my Dell D620 and BCM4311, Please help:confused:

---


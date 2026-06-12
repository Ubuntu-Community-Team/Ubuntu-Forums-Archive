---
title: "Realtech 8139 network cards"
date: 2009-12-15
forum: Hardware
---

### Post by unavenged on 2009-12-15
Hi,

I have an old PC that im trying to set up for a VPN server with Jaunty server, It has an onboard Realtek "Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)" and i installed an extra network card with the same chipset... I've been trying to set up the second card with no luck..

I have tried this to see if it might be the driver
```
sudo modprobe 8139too
```

And tried adding pci=nopci as a booting option(not sure if this is right)

```
kernel          /vmlinuz-2.6.28-11-server root=/dev/mapper/Pebkac-root ro quiet splash pci=noacpi
```

When i edit the network interfaces file and reload the network with
```
sudo /etc/init.d/networking force-reload
```

I get the following
```
bob@Pebkac:~$ sudo /etc/init.d/networking force-reload
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
                                                                         [ OK ]
```

Thanks in advance

---

### Post by unavenged on 2009-12-15
I also tried te following
```
bob@Pebkac:~$ sudo lshw -c network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:d0:c9:28:75:65
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=172.16.20.125 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 14
       bus info: pci@0000:00:14.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=64 mingnt=32

```

I read on another forum that "network:1 UNCLAIMED" means that the driver isn't loading right... so i did

```
sudo rmmod 8139cp
sudo rmmod 8139too
sudo modprobe 8139too

```

But i get this error

```
WARNING: All config files need .conf: /etc/modprobe.d/second-card, it will be ignored in the future release.
[26247.880173] 8139too 0000:00:14.0: region #0 not a PIO resource, aborting
```

---

### Post by unavenged on 2009-12-15
in dmesg i found this

```
[    6.967671] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.967808] 8139cp 0000:00:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    6.967867] 8139cp 0000:00:14.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    7.009338] 8139too Fast Ethernet driver 0.9.28
[    7.009531] 8139too 0000:00:0a.0: found PCI INT A -> IRQ 11
[    7.009572] 8139too 0000:00:0a.0: sharing IRQ 11 with 0000:00:07.2
[    7.009609] 8139too 0000:00:0a.0: sharing IRQ 11 with 0000:00:14.0
[    7.013175] eth0: RealTek RTL8139 at 0xd400, 00:d0:c9:28:75:65, IRQ 11
[    7.013193] eth0:  Identified 8139 chip type 'RTL-8139B'
[    7.013296] 8139too 0000:00:14.0: enabling device (0000 -> 0002)
[    7.013321] 8139too 0000:00:14.0: found PCI INT A -> IRQ 11
[    7.013360] 8139too 0000:00:14.0: sharing IRQ 11 with 0000:00:07.2
[    7.013379] 8139too 0000:00:14.0: sharing IRQ 11 with 0000:00:0a.0
[    7.013416] 8139too 0000:00:14.0: region #0 not a PIO resource, aborting

```

Looks like an IRQ issue? or am i wrong?

---

### Post by unavenged on 2009-12-15
I tried adding this to "/boot/grub/menu.lst" with no luck

```
noapic nolapic acpi=off pci=noacpi
```

---

### Post by unavenged on 2009-12-16
Hi, I found an option in the BIOS that said something about "PNP os" and i set it to yes, now i have a new error in dmesg

```
[    7.018728] 8139too 0000:00:14.0: Chip not responding, ignoring board
[    7.018831] 8139too: probe of 0000:00:14.0 failed with error -5

```

---


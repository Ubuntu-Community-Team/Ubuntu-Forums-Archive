---
title: "Driver for my wifi"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by xodeus on 2008-02-26
Hi there. I need a driver for this device.
I can see that madwifi doesn\t support it.

0c:00.0 Network controller: RaLink Unknown device 0781
        Subsystem: RaLink Unknown device 2790
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f8200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

---

### Post by jan quark on 2008-02-27
what is the output from ?

```
lspci
```
```

sudo lshw -C network
```

---

### Post by xodeus on 2008-02-28
```
[root@localhost guest]# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: RaLink Unknown device 0781
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0e:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
[root@localhost guest]#                                                      
```

```
[root@localhost guest]# lshw -C network
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:cb:c8:d2
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.0.182 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
[root@localhost guest]# 
```

This is what I get. Not much info about the ralink stuff.

---

### Post by PacShady on 2008-03-31
I have the same card in my new laptop. Any news on how to get this card up and running?

'Shady

---

### Post by xodeus on 2008-04-01
Yeah, this is ralink rt2860 sta.
You can get it running with the driver from ralink.
You just have to compile it first.
But you can not yet compile it on a 2.6.24 and newer linux...
Have to use 2.6.23 or below.

[http://www.ralinktech.com.tw/data/drivers/2008_0108_RT2860_Linux_STA_v1.5.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0108_RT2860_Linux_STA_v1.5.0.0.tar.bz2)

---

### Post by xodeus on 2008-04-07
Good news everyone.
ralink has just mailed me a new version of this driver.
Get the source and compile you version from here
[http://www.ralinktech.com.tw/data/drivers/2008_0325_RT2860_Linux_STA_v1.6.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0325_RT2860_Linux_STA_v1.6.1.0.tar.bz2)

compiles and install fine with linux 2.6.24

---


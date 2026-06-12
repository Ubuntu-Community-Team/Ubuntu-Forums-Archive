---
title: "trouble getting Intel WiFi card to work"
date: 2011-11-19
forum: Hardware
---

### Post by pvermees on 2011-11-19
I installed Ubuntu 10.04 on a Samsung NC110-A06UK netbook, but can't get the wireless internet to work. I followed the online troubleshooting guide but with no luck so far after hours of trying. I'm a relative newbie at these things and was wondering if anyone could tell me whether there's any hope of getting this thing to talk to the router.

```
pvermees@pv-netbook:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E8:11:32:D0:29:AA

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```

and

```
pvermees@pv-netbook:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f0101fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: e8:11:32:d0:29:aa
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:2000(size=256) memory:f050c000-f050cfff(prefetchable) memory:f0508000-f050bfff(prefetchable)

```

and finally

```
pvermees@pv-netbook:~$ sudo lspci -nn | grep 0280
05:00.0 Network controller [0280]: Intel Corporation Device [8086:0896] (rev 34)

```

There is a website called intellinuxwireless.org with a list of Intel drivers but based on the above information, I can't figure out which driver to download.

Any help would be much appreciated!

---


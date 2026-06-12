---
title: "Problems With ndiswrapper"
date: 2011-01-14
forum: Hardware
---

### Post by earnshae on 2011-01-14
Hello,

I have been having some problems with ndiswrapper and was hoping someone mights have some advice or could point me at a good reference.

First off I have had wireless working with this computer for over a year. I did something to mess it up I am not sure what but now I don't seem to have any wireless card drivers, or they have become invalid because I can no longer connect to my wireless network.

Here is some system information:

Ubuntu 10.04(64bit)

```
lspci | grep Network
```

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

```
iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

vbox0     no wireless extensions.

cat /etc/network/interfaces

#auto eth0

auto eth1
iface eth1 inet dhcp
iface eth0 inet dhcp

auto lo
iface lo inet loopback

```
ndiswrapper -l
```

b57nd60x : invalid driver!
b57win32 : invalid driver!

```
lshw -C network
```
 *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 03
       serial: 00:23:4e:ab:eb:96
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f1ffc000-f1ffffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:ea:19:2f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v3.04 ip=192.168.2.2 latency=0 multicast=yes
       resources: irq:30 memory:f1bf0000-f1bfffff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: vbox0
       serial: 0a:2e:8c:7c:6a:59
       capabilities: ethernet physical
       configuration: broadcast=yes driver=tun driverversion=1.6 firmware=N/A multicast=yes
```
cat /proc/net/dev
```
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:     720      12    0    0    0     0          0         0      720      12    0    0    0     0       0          0
  eth0: 3026994    4267    0    0    0     0          0       260   798497    4259    0    0    0     0       0          0
  eth1:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
vboxnet0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
 vbox0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0



I have tried looking through a number of tutorial/documentation, at this point I am hoping some new ideas, from outside the box might help me.

---


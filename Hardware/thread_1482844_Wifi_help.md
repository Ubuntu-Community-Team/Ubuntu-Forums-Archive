---
title: "Wifi help"
date: 2010-05-14
forum: Hardware
---

### Post by Wish4Me on 2010-05-14
[http://www.amazon.com/gp/product/B0037G2BMY/ref=oss_product](http://www.amazon.com/gp/product/B0037G2BMY/ref=oss_product)

I bought this because it said it worked with Linux. It apears to use a Ralink Chipset. Works fantastic outstanding for my Windows 7 installation. I know it should work with the fresh Kubuntu 10.4 I just installed. Can I get some documentation on how to set it up properly or something please.

---

### Post by Zorael on 2010-05-17
Paste the output of the following commands entered in a terminal.
```
lsusb

lshw -c network

iwconfig
```
(Paste it inbetween code tags to make it easy on the eyes.)

---

### Post by Wish4Me on 2010-05-18
```
wish4me@Comp:~$ lsusb
Bus 009 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 046d:c069 Logitech, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
wish4me@Comp:~$ sudo lshw -c network
[sudo] password for wish4me: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:24:1d:d9:1a:66
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:33 ioport:ce00(size=256) memory:fbdff000-fbdfffff(prefetchable) memory:fbdf8000-fbdfbfff(prefetchable) memory:fbd00000-fbd1ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:a1:b0:2c:03:f5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
wish4me@Comp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

This is what it shows. The bolded is important I think.

---

### Post by Zorael on 2010-05-18
It seems to be detected and loaded properly, at least to the extent that a wlan0 interface has been created.

And you can't just connect via the network management plasmoid? What happens?

---

### Post by Wish4Me on 2010-05-19
What happens is nothing. When I press scan nothing comes up. And when I manually enter everything it doesn't connect. Its as if the adapter isn't connected or its not reading it or something.

---


---
title: "Ubuntu 18.04.3 LTS Wired Connection Problems"
date: 2020-01-08
forum: Hardware
---

### Post by saxophonix on 2020-01-08
Hi there,

Currently I am new to Ubuntu and have currently have 18.04 installed. However, my wired connection keeps randomly dropping to 10MB/s, where as it should be at 1000MB/s. I've tried running 'apt install r8168-dkms' to change the driver, but this didn't solve the solution long term. Sometimes if I change Ethernet cables the connection will go back up to where it should be, however it keeps dropping eventually. Any help would be appreciated, cheers :)

Output of 'sudo lshw -C network'
```

*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 15
       serial: 3c:52:82:31:bf:0d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=yes multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:3000(size=256) memory:ceb04000-ceb04fff memory:ceb00000-ceb03fff
  *-network
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 59
       serial: c8:21:58:c2:77:39
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-37-generic firmware=29.1044073957.0 ip=10.10.11.23 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:129 memory:cea00000-cea01fff

```

Again I am relatively new to Ubuntu so let me know if theres any more info I can show.

---

### Post by TheFu on 2020-01-08
How does it work if you boot from a flash drive and use the "Try Ubuntu" option?  Does it drop back?
Have you tried using different switch ports?
Also, be certain not to enable the wifi connection at all.  That will mess with routing, though it shouldn't impact a GigE reported connection.

You are experiencing one of the reasons I avoid Realtek network devices and prefer Intel. I think I have the same type of realtek on 1 of my cheap system here, probably not the same version (15) that you have.  Mine is version "0c" and uses the driver=r8169.  If you install that and blacklist the r8168 driver, it might be better, but I wouldn't count on it.  

This stuff is very specific to the exact chips in your machine and might only be an issue with the switch port.  Test that by using a different computer with GigE using the same CAT5e and switch port.

---


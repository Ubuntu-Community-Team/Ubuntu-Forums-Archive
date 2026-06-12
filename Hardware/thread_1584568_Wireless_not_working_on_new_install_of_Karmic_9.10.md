---
title: "Wireless not working on new install of Karmic 9.10"
date: 2010-09-29
forum: Hardware
---

### Post by Mylorharbour on 2010-09-29
I've installed Karmic on a Dell Latitude D505. The install spotted the Broadcom wireless card and I accepted the option to download and install the Broadcom B43 wireless driver. I left click on the network icon, top right, but under the greyed out Wireless Network is says 'Device not ready'

Where should I go from here?

lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fcffc000-fcffdfff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 81
       serial: 00:11:43:39:b6:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.0.18 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:fcffe000-fcffefff ioport:ecc0(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:09:0c:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by lukeiamyourfather on 2010-09-29
Is there a physical switch on the machine to enable and disable wireless radios? I have a ThinkPad with a physical switch for the wireless radios and when set to off that's what I get when clicking the network icon.

---

### Post by Mylorharbour on 2010-09-29
Thanks for the quick reply.
Fn-F2 should turn wireless on and off but it makes no difference.

---

### Post by Mylorharbour on 2011-01-13
Just to close off this old thread, the screen died a few days later so in the skip it went.

---


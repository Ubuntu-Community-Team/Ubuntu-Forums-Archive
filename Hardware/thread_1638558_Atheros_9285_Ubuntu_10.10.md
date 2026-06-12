---
title: "Atheros 9285 Ubuntu 10.10"
date: 2010-12-05
forum: Hardware
---

### Post by PutzFrau on 2010-12-05
Hi there!

I have a Lenovo Z360 and I have Ubuntu 10.10 installed (32bit as well as 64bit). I have an Atheros 9825 WLAN controller, but it does not work in either of those OS.

lspci | grep Wir
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

uname -r
2.6.35-23-generic

iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

sudo lshw -C Network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 70:f1:a1:aa:92:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-23-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f050ffff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c1
       serial: c8:0a:a9:cc:f0:fa
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=129.206.174.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:47 memory:f0400000-f043ffff ioport:3000(size=128)


I am rather new to Linux (10.10 is the first distribution I use).
I have tried several workarounds (all of them were supposed to work on older Kernels), but none of them worked for me.
If you need any additional information, just let me know.

Cheers and thanks for any help!

---

### Post by Lucian_Nilo on 2010-12-07
I'm having the same problem. Did you get it figured out?

---

### Post by PutzFrau on 2010-12-08
No, not yet. I think, this should be moved to the networking forums, wasn't aware of that when I opened this topic.

---

### Post by jepong on 2010-12-16
same here... the only i get out of google is this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660864)

---

### Post by PutzFrau on 2010-12-20
Didn't have access to the internet during the last days. I'll check that site out and see whether it is of any help to me.
Cheers.

---


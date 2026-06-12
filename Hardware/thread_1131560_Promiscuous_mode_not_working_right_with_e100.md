---
title: "Promiscuous mode not working right with e100"
date: 2009-04-20
forum: Hardware
---

### Post by foamz on 2009-04-20
I have a HP530 laptop with Ubuntu 8.10. The problem I have is with my onboard network card... it doesn't go properly into promiscuous mode.

When I fire up wireshark or tcpdump I can see in /var/log/messages that the card goes into and out of promiscuous mode as I start and stop it. Although the only traffic I see is my own traffic. I can create traffic until I'm blue in the face on all other pc's on the network, but I only see my traffic. My card uses the e100 driver, below is all the details I think is needed.

Does anyone have suggestions what I can do to get promiscuous mode to work right?

uname -a:
Linux mezmerize 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

lspci:
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)

lshw -C network:
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:30:3b:81
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

tail -f /var/log/messages:
Apr 21 14:05:26 mezmerize kernel: [49483.148070] device eth0 entered promiscuous mode
Apr 21 14:05:59 mezmerize kernel: [49516.744043] device eth0 left promiscuous mode


Any help will be appreciated.

---

### Post by foamz on 2009-04-23
*bump*

---


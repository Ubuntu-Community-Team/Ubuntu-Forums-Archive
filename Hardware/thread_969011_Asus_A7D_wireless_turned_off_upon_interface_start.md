---
title: "Asus A7D wireless turned off upon interface start"
date: 2008-11-03
forum: Hardware
---

### Post by dranick on 2008-11-03
Hello,

I have an Asus A7D with a  Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) network card.

Upon system loading the card gets started (the wireless led turns on) but as soon as the login comes up the led goes off.

I can see my wireless network upon clicking on the network manager but I can't connect to it (it asks for authentication but it does not connect to the wireless router even if I supply the password - the authentication is WPA Personal).

I have the following output on a lshw -C network command:

```

  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: wlan0
       version: 02
       serial: 00:17:31:2f:fd:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

Ubuntu version: 8.10 with the latest updates installed. System is x86_64.

Please help!

Thank you,

Nick

---

### Post by dranick on 2008-11-07
***bump***

---


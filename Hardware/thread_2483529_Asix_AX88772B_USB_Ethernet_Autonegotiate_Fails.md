---
title: "Asix AX88772B USB Ethernet Autonegotiate Fails"
date: 2023-02-02
forum: Hardware
---

### Post by otterc on 2023-02-02
I've been using an ASIX USB Network Adapter with Ubuntu 19 previously which was working. I just upgraded to 22.04.1LTS and the autonegotiate feature is no longer working.  
It only works if I run:
ethtool -s {Interface} autoneg off speed 100 duplex full
Otherwise it never gets an IP, and displays "Cable Unplugged"
With Windows on the same computer it's working ok.

Any ideas what I can try?..

I also tried this USB Adapter on the latest Linux Mint on another computer, and the same problem happened.
This is what it ends up looking like when plugged in:

  *-network
       description: Ethernet interface
       physical id: c
       bus info: usb@3:3
       logical name: enx000000092521
       serial: 00:00:00:09:25:21
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Dec-2011 firmware=ASIX AX88772B USB 2.0 Ethernet link=no multicast=yes port=twisted pair

I'm not sure how the OS can affect autonegotiation .. but it worked on Ubuntu 19 and Windows.
Any help is appreciated.

---


---
title: "Problem with Linksys wpc300n"
date: 2008-08-24
forum: Hardware
---

### Post by Tofiy on 2008-08-24
My UBANTU doesnt want to see my Linksys device, conneced to PCMCIA.
I Installed Windows drivers support, installed wireless card drivers, and in "Wireless Network Drivers menu" it says that device present. 
But device doesnt show up if i put in command "sudo lshw"
Also the lights dont come up on wireless PCIMCIA card.
Any ideas anybody?

---

### Post by Tofiy on 2008-08-24
This is the only thing that lshw shows


 *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 41
       serial: 00:02:3f:35:10:95
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:07:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       configuration: latency=0


And thats is not my wireless that is my lan card.

---

### Post by wreckedcarzz on 2008-09-01
I have the same problem - Ubuntu Hardy doesn't see the WPC300N. I tried a beta kernel update I found somewhere on the forums a couple of weeks ago, to no avail.

Is it true that the next major Ubuntu update will finally feature wireless N support? Or are us next-gen users just stuck back on old school ethernet connections?

---


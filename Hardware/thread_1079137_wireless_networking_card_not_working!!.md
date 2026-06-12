---
title: "wireless networking card not working!!"
date: 2009-02-24
forum: Hardware
---

### Post by mdinh on 2009-02-24
hey there everyone im new to ubuntu and i just installed ubuntu 8.10 on my compaq laptop and everything works fine except for the wireless networking
under system/administration/hardware drivers it says that support for my Atheros 802.11 wireless LAN card is activated, but in the terminal it says that its not working

minh@minh-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:4d:af:50
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.10.104 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:8b:ce:75:ca:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


can someone please tell me how to get this network card working properly with VERY DETAILED instructions because i am new to the whole linux thing

thanks in advance to everyone who replied

btw if i have to dl some new drivers or programs or watever to get the network card working can you please provide the links with instructions on how to do everything

---

### Post by binbash on 2009-02-24
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by mdinh on 2009-02-24
i finally fix the problem myself
i spent about 4 hours searching the internet and doing many different things b4 i stumbled upon this site [http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

after following the easy steps i got it working in within 15 minutes and i am completely new to ubuntu

id recommend anyone with the same problem to use this site

---


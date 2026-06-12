---
title: "[SOLVED] wifi help needed please"
date: 2008-12-17
forum: Hardware
---

### Post by meomike2000 on 2008-12-17
just installed ubuntu 8.10 desktop on my dell d410, it has a built in wireless card, card works in xp, but not showing up in ubuntu. from a terminal i used lshw -C network and it shows me :

 *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:00:e5:cf
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
 
but I can not get it to work. this is my first attempt at a wireless card with ubuntu. I do not get why it is not working, any help would be very appreciated.

tia....  mike

---

### Post by iponeverything on 2008-12-18
so is network manager not showing at all?

what do you get from:

```
sudo iwconfig 

```

and 

```
sudo iwlist eth1 scan

```

Make sure you have the latest updates, they just pushed out an update Network Manager the other day.

---

### Post by meomike2000 on 2009-01-07
I have had other problems with this version of ubuntu so i have reverted back to 8.04.1, clean install

---


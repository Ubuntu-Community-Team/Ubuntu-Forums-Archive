---
title: "[SOLVED] wireless on dell laptop not working"
date: 2009-01-07
forum: Hardware
---

### Post by meomike2000 on 2009-01-07
I have installed ubuntu 8.04.1 on my dell latitude d410. all went well everything seems to work exept my built in wireless. I have never set up a wireless connection with ubuntu. also I will not always be using the wireless, will use a wired connection when possible, if that matters.

when I boot in windows, also still on machine, the wireless works and can be turned on/off with the fn+f2 keys. when it is on the light comes on next to the power button. this light is not on in ubuntu and the fn+f2 keys do not turn it on/off in ubuntu.

any help or advice or a link to were I might find some info on this would be great...

thanks in advance,

mike

I ran:

 lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:21:34:6d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5751-v3.29a ip=192.168.1.55 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:00:e5:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

---

### Post by Ahadiel on 2009-01-07
*System => Administration => Hardware Drivers*
See if there are any drivers to install.

---

### Post by meomike2000 on 2009-01-07
there are no drivers listed

---

### Post by meomike2000 on 2009-01-08
well come to find out that the wireless is now working, i had forgot that i had disabled the wireless in my router, and apparently there was no other networks in range. i reset my router and rebooted now it is working, still no wifi enabled light on the display as in windows though... no big deal.

---


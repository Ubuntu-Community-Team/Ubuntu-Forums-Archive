---
title: "belkin wireless g usb adapter"
date: 2009-04-01
forum: Hardware
---

### Post by dharmagio on 2009-04-01
hello

i am trying to install the belkin wireless g usb adapter

i discover that uses a zydas chipset

so following instructions i downloaded the firmware

[http://wiki.zenwalk.org/index.php?title=Zd1211-firmware](http://wiki.zenwalk.org/index.php?title=Zd1211-firmware)

then followed all the instructions correcly

........

problem is that i allready have a working wireless on my laptop
that is a intel agn that is working but it works very slow
example:
downloading ubuntu from same server
ubuntu: between 64-80kbs
win vista: reaches 300kbs

so its a big diference

well my wireless usb belkin doesnt show any activity

and i dont know how to disconect my intel wireless card
because its the only one recognized, dont think it works 
with 2 wireless cards at same time.

someone help me? thanks

---

### Post by argosreality on 2009-04-01
You can run "ifconfig" in the terminal to see your active network connections and then as sudo run "ifconfig wlan0 down" (where wlan0 is your active interface) to disable the current wireless card. 

How are you testing the download speeds? Also, what model Belkin card do you have? I have a Belkin 54G F5D7050 v3 that uses a Ralink chipset.

---

### Post by dharmagio on 2009-04-01
thanks

after reboot
just asked me to do setup a connection
and is now working great with the usb wireless
it was easier than i thougt

but now every time i reboot 
allways do a mess because activates the two wireless at same time
if i cant shut down wlan0 (the laptop wireless) 
is there a way to do a script or some code in the runing aplications,
that following the simple instruction
ifconfig wlan0 down
and turning down the wlan0 before it starts the desktop?

---

### Post by argosreality on 2009-04-02
You might have an option in the BIOS to disable the built in wireless card would be the easiest way. You could also blacklist the built in intel wireless driver if you want as well

lshw -C network

Would show you the drivers for the network devices and then you'd put add the module to /etc/rc.conf (example: !intelnetwork)

I'd go with the BIOS option first though

---

### Post by dharmagio on 2009-04-02
The problem is that my laptop doesnt have that bios option.And i cant find this file rc.conf i think i dont have it.Shood i make one?

---

### Post by dharmagio on 2009-04-30
i am with same problem again
now i want to add this intel wireless connection to the blacklist
but dont know the correct name.
when i do

lshw -C network
*-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1e:8c:28:eb:c9
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A latency=0 link=no module=atl1 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster1
       version: 61
       serial: 00:1d:e0:46:05:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:1c:df:37:3a:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.35 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 66:a3:13:b8:ca:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



this is the wireless i want to add to blacklist,
PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
but allready tried this name and it didnt work
any help?

---


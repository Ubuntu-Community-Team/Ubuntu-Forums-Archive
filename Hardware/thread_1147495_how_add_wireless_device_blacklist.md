---
title: "how add wireless device blacklist"
date: 2009-05-03
forum: Hardware
---

### Post by dharmagio on 2009-05-03
i am with same problem again
i have a intel wireless onboard that i dont want to use
and a belkin usb that i want to use
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

..................................

this is the wireless i want to add to blacklist,
PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
but allready tried this name and it didnt work with
echo 'blacklist (device name)' | sudo tee -a /etc/modprobe.d/blacklist
any help?

---

### Post by 67GTA on 2009-05-03
You need to add the module that your wireless card uses to /etc/modprobe.d/blacklist to disable it. That file is for modules only. Adding device names will do nothing. For Jaunty, it is /etc/modprobe.d/blacklist.conf. Open a terminal and run ```
lspci -vkk
```. Find the device, and it should show wich module it is using. Add that module to the blacklist.

---

### Post by dharmagio on 2009-05-03
thanks it worked

---


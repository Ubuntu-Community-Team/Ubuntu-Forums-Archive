---
title: "Toshiba L650 10.10 wireless issue"
date: 2011-11-29
forum: Hardware
---

### Post by clearedd on 2011-11-29
My wireless connection drops after a min or two of use. I tried disabling and re-enabling and the connection still drops.


I used the method in post #5 to get my wireless connection to show. 

[http://ubuntuforums.org/showthread.php?t=1608908](http://ubuntuforums.org/showthread.php?t=1608908)

> sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dk

> 
chris@chris-ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:05:90:03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192CE driverversion=0005.1116.2010 firmware=56 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:94400000-94403fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: 60:eb:69:c7:6e:ac
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.1.105 latency=0 multicast=yes
       resources: irq:46 memory:93400000-9343ffff ioport:2000(size=128)



---


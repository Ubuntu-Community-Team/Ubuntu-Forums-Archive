---
title: "Hardware driver problem!"
date: 2009-02-03
forum: Hardware
---

### Post by Malvazar on 2009-02-03
Okay I am a noobwhen it come to this stuff so bear with me! I am using an acer aspire running Ubuntu 8.04! I am trying to get my wireless to work! The drivers are installed and I can see all the wireless signals around my area just fine! The problem is that I can't connect to any of them! I would assume it is becouse I can get the drivers for the wireless at activate! And what I mean by that is when I go into to _Hardware Drivers_ section under _System_ - _Administration_ I can see the driver is there and I try the check off the box so the system will start to use it it will tell my I need to restart my computer (note the box has yet to have a check in it!) So I restart the computer and I got check to see if the dirivers are acctivated yet only to find out they are not! (still not check in box and it say that the drivers are not in use) This is really annoying and I am going ot need my wireless next month so I really need some helf ASAP! PLEASE!!!!!!!!!

If you need more info please ask!

---

### Post by mikewhatever on 2009-02-04
Wireless drivers, even if from the restricted section, are usually enabled by default, and in case you can see the wireless networks around you, the driver is definitely loaded. Post some info about you wireless hardware, perhaps someone can help.

---

### Post by Malvazar on 2009-02-04
Umm... my wireless card is a Atheros 802.11 according the the according to the hardware dirver thing.

---

### Post by mikewhatever on 2009-02-04
You need to post the outputs of the following:
sudo lshw -C network
ifconfig
iwconfig

---

### Post by dariem on 2009-02-04
I just installed a new sound card on computer how start rescan hardware and automatically download and install driver for this new sound card.

Thank you,

---

### Post by mikewhatever on 2009-02-04
> **dariem said:**
> I just installed a new sound card on computer how start rescan hardware and automatically download and install driver for this new sound card.

Thank you,

Please start your own thread.

---

### Post by Malvazar on 2009-02-04
> **mikewhatever said:**
> You need to post the outputs of the following:
sudo lshw -C network
ifconfig
iwconfig
Ummm.... not sure how you want me to post the output so I just put in the three commands one right after the other and this is what cam out!

malvazar@malvazar-laptop:~$ sudo lshw -C network
[sudo] password for malvazar: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:5e:9f:75
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.102 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:1d:d9:2a:47:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,06/05/2007,6.0.3.85 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
malvazar@malvazar-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:5e:9f:75  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe5e:9f75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9762038 (9.3 MB)  TX bytes:733070 (715.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63800 (62.3 KB)  TX bytes:63800 (62.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:2a:47:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:54100000-54110000 

malvazar@malvazar-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

malvazar@malvazar-laptop:~$

---

### Post by Malvazar on 2009-02-07
Comon guy! I really could use some help here...

---


---
title: "WNC-0305USB wlan adapter doesn't work"
date: 2008-09-03
forum: Hardware
---

### Post by kogia on 2008-09-03
hi. my WNC-0305USB wlan adapter doesn't work in ubuntu 8.04.is there any ideas how to make it work?

---

### Post by falcon61102 on 2008-09-03
Alright, well we're going to need some more information about your computer and your hardware in particular.  If you could, open up a terminal, run the following commands and post the results here:
```
sudo lshw -C network
sudo lspci -nn
```

That will give us some more info to work with.

---

### Post by kogia on 2008-09-03
the results for sudo lshw -C network are:

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 20
       serial: 00:08:02:d0:ba:d4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139cp driverversion=1.3 duplex=full ip=192.168.178.22 latency=64 link=yes maxlatency=64 mingnt=32 module=8139cp multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:6b:19:9c:df
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


the results for sudo lspci -nn are:

00:00.0 Host bridge [0600]: ATI Technologies Inc AGP Bridge [IGP 320M] [1002:cab0] (rev 13)
00:01.0 PCI bridge [0604]: ATI Technologies Inc PCI Bridge [IGP 320M] [1002:700f] (rev 01)
00:02.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller Audio Device [10b9:5451] (rev 02)
00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 20)
00:0c.0 Communication controller [0780]: Conexant HSF 56k HSFi Modem [14f1:2f00] (rev 01)
00:0f.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:10.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:11.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility U1 [1002:4336]

---

### Post by kogia on 2008-09-03
the results for sudo lshw -C network are:

*-network 
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: b
bus info: pci@0000:00:0b.0
logical name: eth0
version: 20
serial: 00:08:02:d0:ba:d4
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139cp driverversion=1.3 duplex=full ip=192.168.178.22 latency=64 link=yes maxlatency=64 mingnt=32 module=8139cp multicast=yes port=MII speed=100MB/s
*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:11:6b:19:9c:df
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


the results for sudo lspci -nn are:

00:00.0 Host bridge [0600]: ATI Technologies Inc AGP Bridge [IGP 320M] [1002:cab0] (rev 13)
00:01.0 PCI bridge [0604]: ATI Technologies Inc PCI Bridge [IGP 320M] [1002:700f] (rev 01)
00:02.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller Audio Device [10b9:5451] (rev 02)
00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 20)
00:0c.0 Communication controller [0780]: Conexant HSF 56k HSFi Modem [14f1:2f00] (rev 01)
00:0f.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:10.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:11.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility U1 [1002:4336]

---

### Post by falcon61102 on 2008-09-03
Well, it's apparent that you need to install some drivers.  If you can not locate any in the repos or from the manufacture, your other option is to use ndiswrapper with some WinXP drivers.  If you can find a set of WinXP drivers for that card, I'll walk you through installing them with ndiswrapper and seeing if that gets it working.

---

### Post by kogia on 2008-09-04
i have win xp drivers for this card

---

### Post by falcon61102 on 2008-09-04
With those drivers you should be able to install them using ndiswrapper.  Whether they will work, I'm not sure but you can give it try.

The first thing you're going to want to do is copy the driver install to Ubuntu.  If you drivers are in a self-extracting exe or a zip file, you can copy the whole file but if they are part of an actual install program, you're going to have to copy the individual files.  If you are unsure, run the program in windows and if it asks you where to extract the drivers before installing then you are good to go.  If not, let me know.

Copy the driver file to your Home folder in Ubuntu.  Then right click and select Extract Here.  That will extract the files to a newly created folder in your Home folder.

Once that is finished, you need to install ndiswrapper.  You can do this without going online by using a LiveCD.  Insert the CD into your drive and start up Synaptic Package Manager from the System>Administration menu.  Once that loads, click File and then Add CDROM...  Go through the menus to add the CD.  Once it completes, run a search for ndiswrapper.  Three things should pop up and if you right click on them, you can Mark for Installation.  Hit apply and let that finish.

The first thing you can try is using ndisgtk which you just installed.  Go to System>Administration>Windows Wireless Drivers.  It should be the last item in the list.  This is the graphical version of ndiswrapper.  You should be able to browse for your drivers if it doesn't detect them automatically, remember they are in your Home directory.  Then go through the install process with those drivers.

Once that completes, check the Network Manager app in the upper right hand corner of the desktop.  See if you can see any wireless access points.  If not, let me know and we'll troubleshoot some.

---

### Post by kogia on 2008-09-04
drivers are an install program and in ubuntu there isn't the option extract here

---

### Post by kogia on 2008-09-04
I did it.i did what u said with drivers but i can't see in the upper right the sign of wlan. I see only the sign of wired network (two screens)

---

### Post by falcon61102 on 2008-09-04
Post the results for:
```
sudo lshw -C network
```
and
```
sudo ndiswrapper -l
```
-l is a lower case L

That will tell us if the drivers installed.

---

### Post by kogia on 2008-09-04
sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 20
       serial: 00:08:02:d0:ba:d4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139cp driverversion=1.3 duplex=full ip=192.168.178.22 latency=64 link=yes maxlatency=64 mingnt=32 module=8139cp multicast=yes port=MII speed=100MB/s


sudo ndiswrapper -l

netrtuw : driver installed
	device (0BDA:8187) present (alternate driver: rtl8187)

---

### Post by lmno149 on 2008-09-04
[everquest 2 plat](http://www.mybloglog.com/buzz/members/everquest_2_plat)[ffxi gil](http://www.mybloglog.com/buzz/members/ffxi_gil/)[gw gold](http://www.mybloglog.com/buzz/members/gw_gold/)[lineage 2 adena](http://www.swagvault.com/lineage-ii-c-21.html  l2 adena  )[lotro gold](http://www.mybloglog.com/buzz/members/lotro_gold/)

---


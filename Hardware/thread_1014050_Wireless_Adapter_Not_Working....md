---
title: "Wireless Adapter Not Working..."
date: 2008-12-17
forum: Hardware
---

### Post by stmasi on 2008-12-17
I guess I'm having issues with my wireless adapter not working. Here's the specs...

Dell Inspiron 600m
2GB PC5300 DDR
250GB HDD
Mobility Radeon 9000
WXGA Display (1400x1050)
BroadCom 570X Gigabit Integrated Controller
Dell Wireless 1450 Dual Band WLAN Mini-PCI Card

So far, just the wireless is not working. However, when I use check the status (disabled,enabled,etc.), it shows up with no status. I can see the device from the network manager, but am apparently unable to use it.

Any ideas?

Thanx.

---

### Post by stmasi on 2008-12-17
Bumpski...

):P

---

### Post by punkybouy on 2008-12-17
Maybe need a driver?  You could use ndiswrapper and load a Windows dot inf file.  What version of Ubuntu are you using?

---

### Post by Ayuthia on 2008-12-17
Have you tried to activate it through System->Administration->Hardware Drivers?   There should be an option for Broadcom in there.  You will need to have a working internet connection because it needs to download some firmware to make it work.

If you have done this already, please post the results of:
```
lspci -nn
lshw -C network
```

---

### Post by stmasi on 2008-12-19
Punkybouy,
I'm using version 8.10.

Ayuthia,
When I go into Hardware Drivers, the entire window is blank...there is nothing listed in that window. As for the results of the two commands you were requesting, here they are:

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)

lshw -C network
*-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a6:07:7a
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.16 latency=32 mingnt=64 module=tg3 multicast=yes
  
*-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

*-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:ae:a1:92
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

*-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 80:00:60:0f:e8:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=169.254.2.2 multicast=yes

*-network:2 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: ea:6f:75:cb:a4:0b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Hopefully, something in there will help solve this problem.

Thanx.

---

### Post by stmasi on 2008-12-19
Buehler...
Buehler...
Buehler...

:lolflag:

---

### Post by stmasi on 2008-12-19
Anyone?

---

### Post by stmasi on 2008-12-29
Whoa...the silence is deafening.

:confused:    [-o<    :cry:

---

### Post by stmasi on 2008-12-29
Yes?

No?

Maybe?

---

### Post by stmasi on 2008-12-30
Well, that's it for me.

Back to Windows.

Ciao.

---

### Post by jd555 on 2009-01-12
I am having a possible related problem w/ the Broadcom adapter in my (oldish) Dell Inspiron 300m. Just now when I cold-booted the machine, the wireless adapter connected and seemed to work fine, but the wired adapter appeared inactive (no corresponding light on the switch, "Auto eth0" was grayed out on the network dropdown). Then it looked like the wired connection came up (no longer grayed out in the dropdown, the wired connection icon was showing in the top menu bar, the corresponding light on the switch indicated a 100mb connection), but then unable to connect to the network, or ping any machines on my local net. So it seems to have taken down the wireless connection (although it too looks okay). Both i'faces have good IP addresses, masks, etc.

I am running Ubuntu 8.10, kernel 2.6.27-9-generic.

The results of the lspci and lshw commands appear below. 

lspci:

00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
02:03.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ac)
02:03.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ac)
02:03.2 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 04)
02:04.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)
02:05.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)

lshw output is (w/ IP addresses futzed with):

  *-network:0
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:e4:a0:16
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.16 ip=64.64.64.204 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:17:fd:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=64.64.64.205 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 92:3f:c0:00:1a:0e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

It looks like the wired connected is disabled, but still being reported as active? I don't know.

Any ideas will be appreciated!

TIA,

jd

---


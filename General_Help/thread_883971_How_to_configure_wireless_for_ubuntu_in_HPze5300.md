---
title: "How to configure wireless for ubuntu in HPze5300"
date: 2008-08-08
forum: General Help
---

### Post by kingkong22 on 2008-08-08
Hi,
  Does anyone give some instructions to configure wireless for ubuntu in HPze5300 ? Thank you so much !!!!!

Regards,

---

### Post by cdtech on 2008-08-08
Please post the output:
```
lspci
```

**Update:**
changed the command.......

---

### Post by kingkong22 on 2008-08-08
*-network:0
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wifi0
       version: 01
       serial: 00:02:8a:99:b1:9d
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.4.9 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:aa:37:2b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s

Sorry for un-edited format !  Thanks a lot.

---

### Post by kingkong22 on 2008-08-08
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

Ok, above is for lspci. Thank you.

---

### Post by cdtech on 2008-08-08
Ok, try this:
```
$ sudo modprobe -r orinoco_pci
$ sudo modprobe -r hostap_pci
$ sudo modprobe -r prism2_pci
$ sudo modprobe orinoco_pci
```
See if that will give you wireless. If it does you'll just have to blacklist the modules above within the "/etc/modprobe.d/blacklist" file.

---

### Post by kingkong22 on 2008-08-08
sudo modprobe -r orinoco_pci

FATAL: Module orinoco_pci not found.

What should I do next ?

---

### Post by cariboo on 2008-08-08
I've got a HP laptop with the same wireless chipset and Hardy and Linux Mint automagically detect and install the drivers  for this chipset. Just left click on the network icon in the panel and choose your network.

Jim

---

### Post by kingkong22 on 2008-08-08
I did. but after I put in passphrase (wireless Security WEP 128-bit passphrase), the network icon just was looping, then agin it pops up the window that askes me to put in passphrase. icon was looping forever. what's issue ? thanks a lot.

---

### Post by kingkong22 on 2008-08-08
Oh ! it does job ! thank you !

---


---
title: "[SOLVED] 8.04 Wireless Network Hardware Issues"
date: 2008-12-31
forum: Hardware
---

### Post by fodd on 2008-12-31
Just recently I created a 3 partition dual boot setup for my old Gateway Laptop (Ubuntu 8.04 boot, FAT32 Shared Partition, Windows XP Pro). Previously I had Ubuntu 8.04 installed on it and it was working flawlessly, but I got tired of running apps on Wine so I decided to create this new setup. The wireless hardware works fine with XP, but when it loads on Ubuntu it will not allow me to enable or disable the hardware through the "Fn" key like it used to do. It also does not detect any wireless networks (which I believe is due to the hardware being disabled).

I checked the wireless internet hardware using,
```
sudo lshw -C network
```
and it showed it up as disabled.

I am fairly familiar with Ubuntu, but have not done a lot of troubleshooting with it because, as I said, it worked flawlessly on my previous install.

If it is necessary I could list what network information was given to me via the code, but I am hoping there is a simple fix. 

Thanks in advance!

---

### Post by melojo on 2008-12-31
if you could post the ouput of

```
lspci
```

and 

```
 sudo lshw -C network
```

this will give us more info.

Also the latest ubuntu release is 8.10 it has better wireless support.

---

### Post by fodd on 2009-01-01
Thanks for the quick response melojo.

Here is the info:

```
sudo lshw -C network
```

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:10:90:ec
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:cb:f7:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```
lspci
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:13.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

Is 8.10 pretty stable? Last I heard I was better off with 8.04 (but that was a while back). I am willing to switch though if it is a stable release and it has better wireless support.

---

### Post by melojo on 2009-01-01
here is a link that might help.  I think this device maybe difficult to get working.
[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)

8.10
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

I would change the title to reflect the name of the wireless card you have and see if someone with the same network device can reply.

maybe
wireless BCM4306 users help

---

### Post by fodd on 2009-01-02
I connected the internet through ethernet and downloaded the package since
```
sudo apt-get install b43-fwcutter
```
could not find the package. I guess all I had to do was hook it up through ethernet and install some updates, one which included the necessary package, then enable it through System->Administration->Hardware Drivers

Problem solved! Thanks for the help!

---


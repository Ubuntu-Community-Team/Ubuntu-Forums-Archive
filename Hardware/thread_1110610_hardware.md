---
title: "hardware"
date: 2009-03-30
forum: Hardware
---

### Post by linderox on 2009-03-30
I have successfully installed bcm43xx for my hp 530 from the same acer aspire 3020 wireless card in ndiswrapper, but "hardware not present" shows me in ndisgtk. (8.04 ubuntu)
I followed by manual [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), but I used ndiswrapper 1.8.

here is my /var/log/messages after starting module ndiswrapper
```

Mar 30 07:47:27 master-laptop kernel: [  255.435118] usbcore: deregistering interface driver ndiswrapper
Mar 30 07:47:27 master-laptop kernel: [  255.454934] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Mar 30 07:47:27 master-laptop kernel: [  255.465922] usbcore: registered new interface driver ndiswrapper

```

```

$uname -m
i686

```
```

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:db:ee:c3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:fa:18:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.36 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

```
```

$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto wlan0
iface wlan inet dhcp
wireless_mode managed
name Wireless_broamcom

```

```

$lspci -nn  
...
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 01)
02:06.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 01)
10:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

```

$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated

```

---


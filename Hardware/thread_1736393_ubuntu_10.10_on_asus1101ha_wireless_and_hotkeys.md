---
title: "ubuntu 10.10 on asus1101ha: wireless and hotkeys"
date: 2011-04-22
forum: Hardware
---

### Post by vevo on 2011-04-22
Hello,

I just installed ubuntu 10.10 on asus 1101ha.
$ uname -a
Linux name 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux

I installed linux-backports-modules-wireless-maverick-generic. However, the wireless is still not working.


Neither the hotkeys are working.

Any solutions?

Thank you in advance
vevo

---

### Post by vevo on 2011-04-23
Hotkeys work by installing compiz:
1. sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update
2. sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config
([http://ubuntuforums.org/showthread.php?t=1260275&page=2](http://ubuntuforums.org/showthread.php?t=1260275&page=2))

---

### Post by varunendra on 2011-04-24
For your wireless problem, please post outputs of:
```
ifconfig -a
```
```
iwconfig
```
```
sudo lshw -C network
```

When you click on NetworkManager icon (upper right corner -> 3 concentric arcs), what all do you see? Is "Enable networking" ticked?

---

### Post by vevo on 2011-04-24
```
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:26:18:ac:51:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:40 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12611 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:406411 (406.4 KB)  Byte TX:406411 (406.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          indirizzo inet:109.55.105.253  P-t-P:10.64.64.64  Maschera:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5622 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:3 
          Byte RX:4730840 (4.7 MB)  Byte TX:982615 (982.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:5f:82:12  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
ppp0      no wireless extensions.

```
```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:18:ac:51:84
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:fbfc0000-fbffffff ioport:e880(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:5f:82:12
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbef0000-fbefffff

```

"Enable networking" is ticked. I am unable to tick "Enable wireless"

---


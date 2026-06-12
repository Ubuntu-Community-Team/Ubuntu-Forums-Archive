---
title: "installing ubuntu over toshiba laptop"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by Housammuhanna on 2008-02-16
i have recently installed ubuntu 7.1 on my toshiba satellite p200-140 every thing goes well axcept my modem, it is not working, i found that driver is not installed after installing gnome-ppp software to establish the connection, can anybody help me with this.
thanks

---

### Post by jan quark on 2008-02-17
ADSL Internet connection using an ethernet PPPoE modem

see this guide
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

for DialUp moden configuration see that guide

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

please run these terminal commands and post the output:

```
iwconfig
```
```
ifconfig
```
```
sudo lshw -C network
```

---

### Post by Housammuhanna on 2008-02-18
Thank you for your reply please find below the result of the three commands you gave to  e:


housam@housam-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

housam@housam-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:FA:D3:9C  
          inet addr:192.168.100.143  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fefa:d39c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39496198 (37.6 MB)  TX bytes:1297872 (1.2 MB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1600 (1.5 KB)  TX bytes:1600 (1.5 KB)

housam@housam-laptop:~$ sudo lshw -C network
[sudo] password for housam:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:fa:d3:9c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.100.143 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


Please find attached the result of the scanmodem command

---


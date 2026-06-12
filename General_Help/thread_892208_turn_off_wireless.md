---
title: "turn off wireless"
date: 2008-08-16
forum: General Help
---

### Post by slickuser on 2008-08-16
I just installed the lastest Ubuntu to my Acer Travelmate C110.

How can disable my wireless, the button my tablet pc doesn't work. I was look at network connection but no help either.

Any help? thanks

---

### Post by tamoneya on 2008-08-16
here is the quick and dirty way:```
sudo ifconfig wlan0 down
```
Then to reenable:```
sudo ifconfig wlan0 up
```

---

### Post by rossjman1 on 2008-08-16
Or you can right click on the wireless bar and deselect "Enable Wireless".

---

### Post by slickuser on 2008-08-17
tamoneya: no device found
slickuser@ubuntu-laptop:~$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device


rossjman1:
I don't see the wireless bar.
I try manual network configuration and un-check the wireless connection.
When I close it and bring up the configuration again. It's checked again.

Any more ideas? Thanks.

---

### Post by tamoneya on 2008-08-17
okay I assumed your wireless was wlan0.  Can we see the output of these commands:```
ifconfig
sudo lshw -C network
```

---

### Post by slickuser on 2008-08-17
output below...

ifconfig

eth0      Link encap:Ethernet  HWaddr 
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe02:9d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39024402 (37.2 MB)  TX bytes:4051588 (3.8 MB)

eth1      Link encap:Ethernet  HWaddr  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x4000 Memory:e0200000-e0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:501600 (489.8 KB)  TX bytes:501600 (489.8 KB)


 sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth1
       version: 04
       serial: 
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated

*-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.5 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by rossjman1 on 2008-08-17
you don't have one of these?
[IMG]https://wiki.thayer.dartmouth.edu/download/attachments/10256864/F8_NMAppletSelectWirelessNet.png[/IMG]

---

### Post by slickuser on 2008-08-18
rossjman1,

I don't have that wireless bar as you show.

Anyway, I messed up with my partition.

I have to re-install it over again.

Let you know if it doesn't show up again.

---

### Post by slickuser on 2008-08-23
This is what I have.

[[IMG]http://img149.imageshack.us/img149/6317/snjg1.th.jpg[/IMG]](http://img149.imageshack.us/my.php?image=snjg1.jpg)

No wireless icon though, but my wireless signal is on. I just want to turn off my wireless signal from my Acer Travelmate C110. The button will not work since I use Ubuntu now. Thanks.

---


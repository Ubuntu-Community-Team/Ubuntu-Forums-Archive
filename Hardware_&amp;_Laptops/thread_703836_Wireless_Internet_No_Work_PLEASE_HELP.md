---
title: "Wireless Internet No Work PLEASE HELP"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by chriscook on 2008-02-21
I just installed ubuntu 7.10 and i can connect to my internet through a hard line *with a wire going to my router* but can't connect to my router wirelessly with the built in wireless card.

i'm using a linksys router, so far i've done....

laptop:~$ sudo lshw -C network
[sudo] password for chris:
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: 10
       serial: 00:11:5b:36:53:92
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.131.4.204 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.8 link=no multicast=yes


laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5B:36:53:92  
          inet addr:10.131.4.204  Bcast:10.131.4.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe36:5392/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6383448 (6.0 MB)  TX bytes:1063597 (1.0 MB)
          Interrupt:5 Base address:0xaf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.


Right, now I don't know what i need to do... Can anyone help???


It dosn't even show a wireless card or network in my network manager. Do i need to install a driver or what? I have a Integrated Wi-Fi-compliant Wireless 802.11b (11 Mbps) LAN not sure what it is tho...thanks.

---

### Post by chriscook on 2008-02-24
no one has any idea?

---


---
title: "Network Card Help"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by klopyrev on 2007-07-19
I urgently need help setting up the network cards on my laptop. I have the following:

IBM Thinkpad T41 2373-311 Laptop
Atheros AR5212 802.11abg Wireless Card
Intel PRO/100/1000 MT 82540EP Ethernet Controller

I am running the following installation:
Ubuntu Feisty Fawn 7.04
Linux 2.6.20-15

I am having the following problems:

1. My wireless cards connects to any unencrypted AP, but it can't connect to any of my home networks that use WEP or WPA encryption.

2. My ethernet card connects to my wired internet, but it works several times slower than the same connection on my Desktop PC, which runs the same Ubuntu and Linux installation. They are even connected to the same router.

I have spent countless hours trying to fix these problems. I have tried installing different version of drivers for both cards. I installed a higher version of madwifi drivers for the wireless card. That didn't help. I read many different forum topics and followed instructions on how to set up madwifi, xsupplicant, wpa_supplicant, etc. I have tried to update my ethernet drivers with e1000, but the make install didn't work, because of some error. I tried disabling ipv6, but I couldn't disable it.

Can someone out there help me out?

---

### Post by anubhavrocks on 2007-07-19
For the Intel PRO/100/1000 MT 82540EP Ethernet Controller

check the output of ifconfig,especially the value of "errors"

and maybe provide more information on how exactly have you determined that the interfaces are slower?

---

### Post by klopyrev on 2007-07-19
eth0      Link encap:Ethernet  HWaddr 00:0D:60:CF:9F:24  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fecf:9f24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1271 errors:52 dropped:0 overruns:0 frame:29
          TX packets:1271 errors:1 dropped:0 overruns:0 carrier:1
          collisions:1 txqueuelen:100 
          RX bytes:1503054 (1.4 MiB)  TX bytes:158579 (154.8 KiB)
          Base address:0x8000 Memory:c0240000-c0260000 

That is the output to ifconfig -v for the ethernet card. As for how I know my connection is slower? My updates takes hours and when I go to speedtest.net, my desktop gets 6000kbs, my laptop gets 600kbs. They are both connected to the same router. Thanks for your reply.

---

### Post by anubhavrocks on 2007-07-19
As you can see from your ifconfig output 

> RX packets:1271 errors:52 dropped:0 overruns:0 frame:29
TX packets:1271 errors:1 dropped:0 overruns:0 carrier:1
collisions:1 txqueuelen:100
RX bytes:1503054 (1.4 MiB) TX bytes:158579 (154.8 KiB)]


a lot of errors are taking place during RX and TX,please start by checking the cable,maybe switching it with your desktop's cable.

---

### Post by klopyrev on 2007-07-20
The cable is fine. I also discovered that when I check my ethernet connection using ethtool eth0, it says that the connection is only 100mbs, when it should be 1000mbs. Any ideas any one?

---

### Post by anubhavrocks on 2007-07-23
Does your router support that speed?

---


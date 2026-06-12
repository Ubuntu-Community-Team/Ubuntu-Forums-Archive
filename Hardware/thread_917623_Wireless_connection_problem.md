---
title: "Wireless connection problem"
date: 2008-09-12
forum: Hardware
---

### Post by smokyboy0 on 2008-09-12
Hi,

I have read through many of similar topics on the forum, but I found no solution to my problem with wireless connection. I have a HP 8710p laptop with Intel 4965AG for wireless networking. I have set up my connection properties according to our network demands (encryptions, keys, certificates). When I try to connect to our institution wireless network, the connection actually succeeds because admin can see me log in. However, my computer does not receive a dynamic IP address afterwards and so I get disconnected.
I am using Ubuntu 8.04 and I connect through NetworkManager. In the System->Network I have a wired connection set to a static IP and a wireless card to roaming mode. I am not sure whether these options could be causing the problem but they do interact with NetworkManager in strange ways.

Anyway, iwconfig shows:

[I]wlan0     IEEE 802.11g  ESSID:"eduroam"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:12:43:8A:7F:A0   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Power Management: off
          Link Quality=56/100  Signal level=-68 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]

And ifconfig wlan0 gives me:

[I]wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:8c:54:e9  
          inet6 addr: fe80::21f:3bff:fe8c:54e9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:390 (390.0 B)  TX bytes:2118 (2.0 KB)
[/I]

If I right clik on the NetworkManager icon and choose Connection information, the IP shown (and all the rest of IPs) is 0.0.0.0.

Does anyone have an idea what could be the problem or at least how to pinpoint the source of it.
Thanks in advance.

---

### Post by bobyy on 2008-09-12
Hy,
Same prob was for me (HP pavilion dv6650)but i removed Netw Manager and instaled Wicd instead...and now it`s ok.

but first try to connect from command line like this :
ifconfig wlan0 down
iwconfig wlan0 mode managed
iwconfig wlan0 essid "your ESSID"
iwconfig wlan0 key *****
ifconfig wlan0 up
dhclient wlan0

if it work in this way just make a script of this and put in /etc/rc.conf

---

### Post by smokyboy0 on 2008-09-12
> **bobyy said:**
> Hy,
Same prob was for me (HP pavilion dv6650)but i removed Netw Manager and instaled Wicd instead...and now it`s ok.

but first try to connect from command line like this :
ifconfig wlan0 down
iwconfig wlan0 mode managed
iwconfig wlan0 essid "your ESSID"
iwconfig wlan0 key *****
ifconfig wlan0 up
dhclient wlan0

if it work in this way just make a script of this and put in /etc/rc.conf

Thanks for your reply. I would gladly try to connect from the prompt but I am afraid the connection settings are quite complicated and I don't know if iwconfig supports them all. For example, in the NetworkManager settings, the connection has TTLS as EAP method, TKIP key type, and PAP Phase2 type. It also requires a password, an identity, an anonymous identity and a CA certificate file specified. I don't see how I could specify all these from the command line using iwconfig options, unless there is some config file that iwconfig uses.

---


---
title: "Wireless Network Connected but no Internet"
date: 2011-06-02
forum: Hardware
---

### Post by jrknox on 2011-06-02
Hello! Just installed Ubuntu 10.4 on my old Dell Inspiron 9200. 

I was able to download the broadcom driver and ubuntu connected to the network. but when I opened firefox I get the Server Not Found error. 

I also tried to ping google: unknown host.

Here is the results of ifconfig and iwconfig

Thanks for the help!

narpas@narpas-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:69:da:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146800 (146.8 KB)  TX bytes:146800 (146.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:17:9f:cb  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:7dff:fe17:9fcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11837 (11.8 KB)

narpas@narpas-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"netgear10"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: B2:F1:95:75:E2:01   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by dandnsmith on 2011-06-03
So far, what you've posted says:
- no IPaddr on ethernet (wired connection), so no possibility there
- IPaddr for IP4 and IP6 on the wireless interface which may mean you've acquired them from a wireless router, but no real traffic.

The 'Server not Found' suggests that DNS resolution isn't functioning - I think there's a good chance that you're not passing the validation stage with the router (but I'm just guessing, here).

If you can look up some site IP addresses (use ping on another installation  which works), and try pinging them, you may be able to localise the problem.

---

### Post by jrknox on 2011-06-03
I tried to ping google and yahoo here are the results:

narpas@narpas-laptop:~$ ping 74.125.225.52
connect: Network is unreachable

narpas@narpas-laptop:~$ ping google.com
ping: unknown host google.com

narpas@narpas-laptop:~$ ping yahoo.com
ping: unknown host yahoo.com

narpas@narpas-laptop:~$ ping 72.30.2.43
connect: Network is unreachable

Thanks for helping me!!

---

### Post by dandnsmith on 2011-06-09
Sorry for not replying - been away in Dublin for a few days.
If you're still stuck, try posting the results of *route* and *ifconfig* when it thinks you're connected.

Those messages you posted say
1) network is unreachable - routing isn't working (wireless not properly connected)
2) unknown host - dns not working (which it couldn't if it couldn't get to the network properly)

---


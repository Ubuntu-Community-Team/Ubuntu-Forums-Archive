---
title: "Edgy: Wireless works; command line only. (Searched forum, no resolution)"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by greatnate on 2006-12-12
I have had a problem for awhile with an intel pro wireless 2100 on my latitude d600.  I have read through the forums however have been unable to find a resolution.

The wireless card "works", that is to say I can scan and connect to an access point using the wireless tools from the command line, use the wireless switch (Fn+F2), see the info in /proc/net/wireless, and see wireless info using iwpriv, however neither wifiradar or network-admin work to configure the wireless card.

I installed the ipw2100 drivers/firmware from sourceforge with no change in behavior.  This was not a problem running dapper.

I was hesitant to post because I was sure I could find an answer on the forums or wiki, however have been unable thus far.

Any help or insight would be greatly appreciated.

```
 dmesg | grep ipw2100:
[17179588.816000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.2.0
[17179588.816000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[17179589.240000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
``````
iwpriv:
lo        no private ioctls.

eth0      no private ioctls.

eth1      Available private ioctls :
          monitor          (8BE0) : set   2 int   & get   0      
          reset            (8BE1) : set   0 int   & get   0      
          set_power        (8BE2) : set   1 int   & get   0      
          get_power        (8BE3) : set   0       & get  80 char 
          set_preamble     (8BE4) : set   1 int   & get   0      
          get_preamble     (8BE5) : set   0       & get  16 char 
          set_crc_check    (8BE6) : set   1 int   & get   0      
          get_crc_check    (8BE7) : set   0       & get  16 char 

sit0      no private ioctls.
``````
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Champion_28thEast"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:51:51:70   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

sit0      no wireless extensions.

``````
ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:0C:F1:3D:52:34  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe3d:5234/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13495 errors:8 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1153454 (1.1 MiB)  TX bytes:5308 (5.1 KiB)
          Interrupt:5 Base address:0x2000 Memory:fafef000-fafeffff 
``````
lsmod | grep ipw:
ipw2100                76720  0 
ieee80211              35272  1 ipw2100
```

---

### Post by Steve S. on 2006-12-13
Did you ever get this working?

I also have been unable to get wireless on edgy, although it ran great in dapper.  

Any insight you might have would be very appreciated.

---

### Post by greatnate on 2006-12-13
I have not.  Since posting I haven't really had time to toy with it.  I was just checking this post for replies.  Hopefully someone will some answers will see it!

---

### Post by gordyt on 2006-12-13
greatnate I can't tell you what is happening with your system, but I did want to say that I've installed 6.10 on an lc2100 system from Linux Certified.  It has that Intel PRO/Wireless 2200, MiniPCI Interface.  I had completely wiped the drive, including all extra stuff that the Linux Certified folks had installed because I was curious how well 6.10 would do with this system.  

In my case the wireless interface is working perfectly (for the first time!).  Detects and connects with my WEP 80211.g network.

--gordy

---

### Post by Patrick-Ruff on 2006-12-15
it's not working because it's not running in gksudo.

I don't know wtf is up, I think a programmer screwed up or something.

---

### Post by greatnate on 2006-12-15
> **Patrick-Ruff said:**
> it's not working because it's not running in gksudo.

I don't know wtf is up, I think a programmer screwed up or something.

Is there some config file or something that can be changed somewhere to fix this?

---

### Post by Patrick-Ruff on 2006-12-15
I don't know, I haven't found it yet :P.  but you can go into the menu editor and edit the command for network settings, that'll work for that, but your menu bar icon for networks, when you click configure, it wont use gksudo :(

---

### Post by greatnate on 2007-01-30
Anyone ever have any luck with this?

---


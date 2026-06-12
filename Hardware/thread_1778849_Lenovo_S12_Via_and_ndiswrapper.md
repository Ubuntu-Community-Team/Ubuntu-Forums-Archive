---
title: "Lenovo S12 Via and ndiswrapper"
date: 2011-06-09
forum: Hardware
---

### Post by cyberfood on 2011-06-09
Hi everyone..

pls can you help me with my problem?  I have Netbook Lenovo Ideapad S12  with cpu Via nano. Since i upgraded my ubuntu to latest version I have  problem with wifi. I have tried install Ndiswrapper, downloaded xp  driver for my book and succesfully implemented. But i dont know to get  list of avaible wifi routers (connetions).

iwconfig returned: 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwlist wlan0 scan returned No scan results.



I have checked link for documentation but on my site it all appears that driver was installed correctly. 

ndiswrapper -l returned 
bcmwl5 : driver installed
    device (14E4:4315) present (alternate driver: ssb)

ip addr returned 
wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:26:82:48:16:56 brd ff:ff:ff:ff:ff:ff

hat i should to do next?

Thank you 
Peter from Slovakia

---


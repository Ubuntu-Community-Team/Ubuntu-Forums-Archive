---
title: "Hp 500 wireless,I am almost collapsed!!!"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by ccbb on 2007-10-10
Hello, everyone. I am almost going to pieces with my wireless. I have googled for several days but could not resolve my problem.

I can find the router throug wifi-radar or iwlist.  The following is the command I used and the result after the command.

sudo iwconfig eth0 essid MX-LINK mode Ad-Hoc channel 6 key restricted s:xxxx-xxxx-xx 
sudo /etc/init.d/networking restart
iwconfig eth0


eth0      IEEE 802.11g  ESSID:"MX-LINK"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 02:16:6F:7C:D9:9A   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-60 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I changed mode to Managed, the Bit Rate said 0, so I think the mode is no problem.
The only problem is maybe the key. I tried very possible combination such as 
key xxxxxxxxxx; key restricted xxxxxxxxxx
key s:xxxxxxxxxx ;key restretricted s:xxxxxxxxxx

My laptop is hp500, wireless is Intel Pro/Wireless 2200BG.

Thank you very much!

BTW: I can access the net in windows!

---

### Post by cubeist on 2007-10-10
Just curios, why aren't you using network manager? Besides that why don't you remove the password from wireless and see if you can connect, at least that way you can rule out if it is just a password problem or if it is general wireless issue.  Also, does you wireless work on other access points?

---

### Post by ccbb on 2007-10-11
I tried network manager, and the same problem. The router is a public one and I don't have the priviilage to modify any settings. Thank you!

---

### Post by cubeist on 2007-10-11
hmm, you are in a bit of a pickle.  The reason I asked about network manager is about TKIP.  Most routers use WPA with TKIP these days and the only way I am able to connect to these routers is through network manager and manually selecting TKIP authentication....but if you are using WEP then disregard this!

---


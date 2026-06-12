---
title: "Newbie - need help with TL-WN951N and Internet Connection"
date: 2010-03-09
forum: Hardware
---

### Post by comprodtv on 2010-03-09
Dear All,
 
Am a newbie to Ubuntu - please be nice/patient with me.
 
Am having issues with Internet Connection using wirless pci card TL-WN951N.
 
_**History:**_
Installed Ubuntu 9.10 (with latest kernel) a few weeks ago on PC. Made this a dual boot with my WinXP SP3. (aim is to eventually ditch WinXP ;)).
 
_PC:_
Mobo: Asus A8N-E
CPU: AMD Athlon 64 3500+
PCI Card: Wirless TP-Link TL-WN951N
TV Card: Compro DVB-T300
and some other stuff....
 
**_Problems:_**
I have issues with the TL-WN951N and Compro DVB-T300. I will start a new thread with the Compro issues...one thing at a time :))
 
_Specific Problems with TL-WN951N:_
Ubunto connects to my router/modem via wifi (or so it says...=connection establised) = great!
But Internet does not work! ------ It works for a few minutes (I can get to url links using FireFox) and ***_then just stops._***
(my laptop connect to router/modem as well, and connects to the internet. so it is not the modem that lost connection)
 
Steps I have taken to try and get it fixed:
1) Went to Network Connections-> DSL -> Edit. Enable Connect Automatically and entered in DSL tab my ISP username and password. 
This did not work, as the problem persists - Internet connection just stops. 
2) Went to System -> Admin -> Network tools and try to ping my router or any url. Nothing! Strange as the Network connection says i am connected.
 
What can i do to get the internet to work, am not sure if this is to do with TL-WN951N or something else.
 
 
help.

---

### Post by comprodtv on 2010-03-17
please help me with this.  any replies will be appreciated.

---

### Post by comprodtv on 2010-03-18
Please note, my Wireless works (pci to router).
But i get internet connection for a few minutes and then it just drops out.  when i reconnect, then i get internet connection again - intermittent and then it drops again (but wireless connection is active) 

I have tried this (and the results are the same as when i have internet connection and when i do not)

iwconfig 
  wlan1     IEEE 802.11bgn  ESSID:"linksys_h"   
           Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:21:CE:8B:28    
           Bit Rate=0 kb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Power Management:on 
           Link Quality=53/70  Signal level=-57 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 


ifconfig 
 wlan1     Link encap:Ethernet  HWaddr 00:27:19:13:e2:31   
           inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::227:19ff:fe13:e231/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1490  Metric:1 
           RX packets:163206 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:57743 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:178202921 (178.2 MB)  TX bytes:6775223 (6.7 MB) 
  
 
sudo route -n   
Kernel IP routing table 
                                 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan1  169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
192.168.1.254   0.0.0.0                         UG    0      0        0 wlan1 



---->  note my router gateway ip is 192.168.1.254.  so it is connecting to router.

 
lspci 
 05:06.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01) 
 

iwlist wlan1 scan 
 wlan1     Scan completed : 
           Cell 01 - Address: 00:24:21:CE:8B:28 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=70/70  Signal level=-35 dBm   
                     Encryption key:on 
                     ESSID:"linksys_h" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                               18 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000005605811bd0 
                     Extra: Last beacon: 2024ms ago 
                     IE: Unknown: 000D6C696E6B7379735F686F6D6532 
                     IE: Unknown: 010882848B961224486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 32048C98B060 
                     IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000 
                     IE: Unknown: 3D160B070700000000000000000000000000000000000000 
                     IE: Unknown: 3E0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                     IE: Unknown: 0B0503000F127A 
                     IE: Unknown: 7F0101 
                     IE: Unknown: DD07000C4304000000 
                     IE: Unknown: 0706415520010D10 
                     IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000 
                     IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000

---

### Post by comprodtv on 2010-03-21
TL-WN951N. (Ubunto 9.10, 2.6.31-20-generic, with driver ath9k). Internet Connection drops after a few minutes (although AP IP is set). Can reconnect using Network Manager (that re-establish connection, but only for a few minutes) Seems the card it is Supported on 9.10 . But ¨Don't know whether IEEE 802.11n works¨ [ https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link") 
 

What I tested:

[U]1) Set AP to broadcast G only - Network Manager
[/U]
Have Set AP to broadcast G+N. Connection drops silently. There is no automatic attempt for reconnection. Manual reconnect is possible via Disconnect / Connect in Network Manager. 
  Have Set AP to broadcast G only.  It now works using Network Manager = no drop-outs 
 

[U]2) Set AP to broadcast G only - Wcid
[/U]
Have Removed NetworkManager and installed Wicd.   
  Have Set AP to broadcast G only.  It now works using Wicd = no drop-outs. 
  Have Set AP to broadcast G+N. Connection drops silently, but less frequent than with Network Manager. There is no automatic attempt for reconnection. Manual reconnect is possible via Disconnect / Connect in Wicd. 
 

Also iwconfig shows Bit Rate=0 kb/s and sometimes Bit Rate=1 Mb/s although connected. Surely this should show 54Mb/s (for G) and 300Mb/s (for N) 

_3) Updated Bug_
[https://dev.openwrt.org/ticket/6667#comment:10](https://dev.openwrt.org/ticket/6667#comment:10)


Suggest this thread to stay open until Ubuntu Supports N with TL-WN951N

---

### Post by Arielxgbarton on 2012-05-06
I am having a similar problem with the same TP-link PCI adapter

It does not work in the mornings (seems very odd):confused:
It sometimes works in the evenings

On the TP-LINK compatibility page (on help.ubuntu.com)
it says
--------------------
Model : TL-WN951N

Chipset : Atheros

Driver : ath9k

Supports Network install : ?

Supported in installed system : Yes

Works 'just out of the box':Yes. Tested on Ubuntu 9.04, 9.10, 10.04

Comments : IEEE 802.11n does not work with 11.04. High Packet loss. Works fine in Wireless G. I believe this is a kernel/driver issue

Last updated : 2011-07-25
--------------------------------------------------------
What is strange is when i had ubuntu 10.04 the wireless did work absolutely perfectly

Yesterday it was only working when i had the side of the computor off:confused:

---


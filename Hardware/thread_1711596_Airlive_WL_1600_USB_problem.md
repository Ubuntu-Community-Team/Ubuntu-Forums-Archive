---
title: "Airlive WL 1600 USB problem"
date: 2011-03-21
forum: Hardware
---

### Post by pkoraca on 2011-03-21
Hello.

I have a DELL vostro A840 laptop with Ubuntu 10.10. Wireless adapter is Atheros Communications Inc. AR5001.
Since the signal is too weak with Atheros, i bought Airlive WL1600 USB adapter. 
On Win7 it worked without any problem, but I had dual-boot and it didn't work on Ubuntu. I thought it was a dual-boot problem because I read that Windows somehow disable WLAN adapter (problem with Wake on LAN), so I did new Ubuntu 10.10 install.
But again, Dell's Atheros works fine on Ubuntu, but Airlive doesn't. It connects to the AP and sometimes at first moment it can go to ie. [www.google.com](www.google.com) but after few seconds it stops. The interface is up, but it doesn't work.


Please help :)



ps. Here are some outputs that may be helpful.


```
iwconfig

wlan1     IEEE 802.11bg  ESSID:"Teo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:68:E0:C3:3D   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:2586-1078-90
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx 

invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lspci -v

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Dell Device 0298
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at de00 [size=256]
	Memory at f6aff000 (64-bit, non-prefetchable) [size=4K]
	Memory at f0000000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at f0020000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
	Capabilities: [cc] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 07-00-00-00-36-4c-e0-00
	Kernel driver in use: r8169
	Kernel modules: r8169

0c:00.0 Network controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Device 1a32:0112
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f6cf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Count=1 Masked-
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Kernel driver in use: ath5k
	Kernel modules: ath5k


dmesg|egrep -i 'fw|wlan'

[    3.056036] firewire_ohci: Added fw-ohci device 0000:03:01.1, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
[    3.548149] firewire_core: created device fw0: GUID 384fc00039c67221, S400
[   19.792818] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  562.631771] wlan0: authenticate with 00:1d:68:e0:c3:3d (try 1)
[  562.633200] wlan0: authenticated
[  562.633219] wlan0: associate with 00:1d:68:e0:c3:3d (try 1)
[  562.635242] wlan0: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[  562.635245] wlan0: associated
[  562.635842] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  571.909227] wlan0: deauthenticating from 00:1d:68:e0:c3:3d by local choice (reason=3)
[ 1650.016493] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2595.528822] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2597.681574] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2957.585214] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2959.623702] wlan0: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 2959.625131] wlan0: authenticated
[ 2959.625149] wlan0: associate with 00:1d:68:e0:c3:3d (try 1)
[ 2959.627927] wlan0: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 2959.627930] wlan0: associated
[ 2959.628838] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2970.144030] wlan0: no IPv6 routers present
[ 3130.581594] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3156.587950] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 1)
[ 3156.784046] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 2)
[ 3156.787197] wlan0: direct probe responded
[ 3156.787207] wlan0: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 3156.799760] wlan0: authenticated
[ 3156.799779] wlan0: associate with 00:1d:68:e0:c3:3d (try 1)
[ 3156.836666] wlan0: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 3156.836670] wlan0: associated
[ 3326.934239] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3329.037449] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3434.697785] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 1)
[ 3434.896048] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 2)
[ 3435.096110] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 3)
[ 3435.296049] wlan0: direct probe to 00:1d:68:e0:c3:3d timed out
[ 3463.691852] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 1)
[ 3463.888039] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 2)
[ 3464.088040] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 3)
[ 3464.288040] wlan0: direct probe to 00:1d:68:e0:c3:3d timed out
[ 3486.687843] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 1)
[ 3486.884045] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 2)
[ 3487.084039] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 3)
[ 3487.284043] wlan0: direct probe to 00:1d:68:e0:c3:3d timed out
[ 3553.915976] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 1)
[ 3554.116044] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 2)
[ 3554.316042] wlan0: direct probe to 00:1d:68:e0:c3:3d (try 3)
[ 3554.516037] wlan0: direct probe to 00:1d:68:e0:c3:3d timed out
[ 3873.736307] wlan0: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 3873.737729] wlan0: authenticated
[ 3873.737748] wlan0: associate with 00:1d:68:e0:c3:3d (try 1)
[ 3873.739767] wlan0: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 3873.739770] wlan0: associated
[ 3873.740799] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3884.496023] wlan0: no IPv6 routers present
[ 4898.209595] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4899.624774] wlan0: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 4899.627873] wlan0: authenticated
[ 4899.627938] wlan0: associate with 00:1d:68:e0:c3:3d (try 1)
[ 4899.643907] wlan0: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 4899.643912] wlan0: associated
[ 4941.157542] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 5041.709283] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5041.711148] wlan1: authenticated
[ 5041.765277] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5041.964044] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5041.965907] wlan1: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 5041.965910] wlan1: associated
[ 5042.023266] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 5052.192027] wlan1: no IPv6 routers present
[ 5242.869324] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5242.871065] wlan1: authenticated
[ 5242.871084] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5243.068034] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5243.268035] wlan1: associate with 00:1d:68:e0:c3:3d (try 3)
[ 5243.468037] wlan1: association with 00:1d:68:e0:c3:3d timed out
[ 5254.973267] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5254.974765] wlan1: authenticated
[ 5255.029263] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5255.228042] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5255.230508] wlan1: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 5255.230511] wlan1: associated
[ 5698.722937] wlan1: deauthenticating from 00:1d:68:e0:c3:3d by local choice (reason=3)
[ 5707.049543] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 5709.229248] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5709.428042] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 2)
[ 5709.430092] wlan1: authenticated
[ 5709.489225] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5709.688034] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5709.888041] wlan1: associate with 00:1d:68:e0:c3:3d (try 3)
[ 5710.088039] wlan1: association with 00:1d:68:e0:c3:3d timed out
[ 5728.241270] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5728.242762] wlan1: authenticated
[ 5728.293259] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5728.492035] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5728.494379] wlan1: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 5728.494382] wlan1: associated
[ 5728.550855] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 5738.768034] wlan1: no IPv6 routers present
[ 5768.410147] device wlan0 entered promiscuous mode
[ 5769.784353] device wlan0 left promiscuous mode
[ 5771.098127] device wlan1 entered promiscuous mode
[ 5774.618831] wlan1: deauthenticating from 00:1d:68:e0:c3:3d by local choice (reason=3)
[ 5776.850161] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 5779.084479] device wlan1 left promiscuous mode
[ 5788.322720] device wlan1 entered promiscuous mode
[ 5791.354613] device wlan1 left promiscuous mode
[ 5793.481487] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 5795.649318] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5795.651058] wlan1: authenticated
[ 5795.705315] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5795.904041] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5795.905937] wlan1: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 5795.905940] wlan1: associated
[ 5795.966867] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 5796.034686] device wlan1 entered promiscuous mode
[ 5806.472029] wlan1: no IPv6 routers present
[ 5821.291831] device wlan1 left promiscuous mode
[ 5833.498795] wlan1: deauthenticating from 00:1d:68:e0:c3:3d by local choice (reason=3)
[ 5835.705588] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 5837.442124] device wlan1 entered promiscuous mode
[ 5843.753229] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5843.754714] wlan1: authenticated
[ 5843.817335] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5844.016047] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5844.018454] wlan1: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 5844.018457] wlan1: associated
[ 5844.075316] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 5854.424027] wlan1: no IPv6 routers present
[ 5892.366635] wlan1: deauthenticating from 00:1d:68:e0:c3:3d by local choice (reason=3)
[ 5894.565460] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5894.566973] wlan1: authenticated
[ 5894.617217] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5894.816041] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5894.818337] wlan1: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 5894.818340] wlan1: associated
[ 5899.864353] device wlan1 left promiscuous mode
[ 5904.762831] wlan1: deauthenticating from 00:1d:68:e0:c3:3d by local choice (reason=3)
[ 5906.646224] device wlan1 entered promiscuous mode
[ 5912.877258] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5912.879124] wlan1: authenticated
[ 5912.929260] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5913.128034] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5913.129883] wlan1: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 5913.129886] wlan1: associated
[ 5995.238239] wlan1: deauthenticated from 00:1d:68:e0:c3:3d (Reason: 7)
[ 5997.473244] wlan1: authenticate with 00:1d:68:e0:c3:3d (try 1)
[ 5997.474854] wlan1: authenticated
[ 5997.474872] wlan1: associate with 00:1d:68:e0:c3:3d (try 1)
[ 5997.672034] wlan1: associate with 00:1d:68:e0:c3:3d (try 2)
[ 5997.674471] wlan1: RX AssocResp from 00:1d:68:e0:c3:3d (capab=0x411 status=0 aid=1)
[ 5997.674474] wlan1: associated
[ 6179.216419] device wlan1 left promiscuous mode
```

---


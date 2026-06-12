---
title: "Wireless Network not working in Ubuntu"
date: 2012-02-07
forum: Hardware
---

### Post by ganesh3 on 2012-02-07
Hi,

I am using Ubuntu 11.10 with 3.0.0.15 kernel.

I have a wireless router which I use to connect to the internet but lately I have been facing issues connecting to internet.

I tried pinging website which would work properly but after some time would give this error:
ping: sendmsg: No Buffer space available.

I am not sure what is the problem as I have another laptop which has Windows in it and the internet is working fine.

Please note I am an amateur with Ubuntu so if you need any information please let me know the steps along with the command to be run.

Please help in solving the issue.

Thanks,

Ganesh Bhat.

---

### Post by ganesh3 on 2012-02-08
It would be great if someone could please help with the problem.

Also, Please note I am using the Broadcom STA wireless driver which was downloaded by default when I had installed ubuntu for the first time.

Thanks & Regards,

Ganesh Bhat.

---

### Post by madvinegar on 2012-02-08
> **ganesh3 said:**
> It would be great if someone could please help with the problem.

Also, Please note I am using the Broadcom STA wireless driver which was downloaded by default when I had installed ubuntu for the first time.

Thanks & Regards,

Ganesh Bhat.

Please open a terminal and write

```
lspci
```

and post here the results.

---

### Post by ganesh3 on 2012-02-08
PFA the results of the command.


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
04:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
07:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by madvinegar on 2012-02-09
Your wireless card is the following:

04:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)


Do the following:

Open synaptics package manager and mark for installation the following two packages:

- b43-fwcutter
- firmware-b43-installer

Click apply to install them. (you may need to plug an ethernet cable first from your router in order to get internet connection).

(Please also make sure that the package "firmware-b43-ipphy-installer" is **not** installed).


Then go to additional drivers and **DE**-activate the recomended broadcom STA wireless driver.

Restart and let me know.

---

### Post by ganesh3 on 2012-02-09
Hi,

Thanks for the suggestion, but it hasn't worked.

It would be great if you coulld help me with some other steps to rectify the problem.

Regards,

Ganesh Bhat

---

### Post by madvinegar on 2012-02-09
Could you also please open a terminal and post the results of the following commands?

```
ifconfig -a
```
```
dmesg | grep -i wlan
```
```
dmesg | grep -i wireless
```
```
iwconfig wlan0
```

---

### Post by ganesh3 on 2012-02-09
Here you go!!!

ifconfig -a
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:51:90:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:834914 (834.9 KB)  TX bytes:834914 (834.9 KB)

wlan0     Link encap:Ethernet  HWaddr c4:17:fe:d7:67:3c  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::c617:feff:fed7:673c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:36996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30780391 (30.7 MB)  TX bytes:7006642 (7.0 MB)
----------------------------------------------------------------------------------------------------------------------

dmesg | grep -i wlan
[   26.221010] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.118046] wlan0: authenticate with 00:22:75:e0:fd:86 (try 1)
[   33.119597] wlan0: authenticated
[   33.123912] wlan0: associate with 00:22:75:e0:fd:86 (try 1)
[   33.127923] wlan0: RX AssocResp from 00:22:75:e0:fd:86 (capab=0x411 status=0 aid=1)
[   33.127929] wlan0: associated
[   33.129645] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.099354] wlan0: no IPv6 routers present
[   45.685702] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=192.168.2.1 DST=192.168.2.5 LEN=311 TOS=0x00 PREC=0x00 TTL=64 ID=38211 PROTO=UDP SPT=1900 DPT=46236 LEN=291 
[  367.624092] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=64.27.101.155 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x00 TTL=239 ID=0 PROTO=TCP SPT=80 DPT=56253 WINDOW=0 RES=0x00 RST URGP=0 
[  396.974801] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=203.94.209.18 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=0 DF PROTO=TCP SPT=80 DPT=58316 WINDOW=0 RES=0x00 RST URGP=0 
[  397.719876] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=203.94.209.18 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=0 DF PROTO=TCP SPT=80 DPT=58314 WINDOW=0 RES=0x00 RST URGP=0 
[  397.719994] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=203.94.209.18 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=0 DF PROTO=TCP SPT=80 DPT=58314 WINDOW=0 RES=0x00 RST URGP=0 
[  397.720152] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=203.94.209.18 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x00 TTL=59 ID=0 DF PROTO=TCP SPT=80 DPT=58315 WINDOW=0 RES=0x00 RST URGP=0 
[  402.146958] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=75.126.18.100 DST=192.168.2.5 LEN=605 TOS=0x00 PREC=0x00 TTL=53 ID=20932 DF PROTO=TCP SPT=80 DPT=58646 WINDOW=56 RES=0x00 ACK FIN URGP=0 
[  436.669833] wlan0: authenticate with 00:22:75:e0:fd:86 (try 1)
[  436.672922] wlan0: authenticated
[  436.673442] wlan0: associate with 00:22:75:e0:fd:86 (try 1)
[  436.679393] wlan0: RX ReassocResp from 00:22:75:e0:fd:86 (capab=0x411 status=0 aid=1)
[  436.679400] wlan0: associated
[  440.087282] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=75.126.18.100 DST=192.168.2.5 LEN=264 TOS=0x00 PREC=0x00 TTL=53 ID=30765 DF PROTO=TCP SPT=80 DPT=58705 WINDOW=46 RES=0x00 ACK FIN URGP=0 
[  455.425707] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=204.246.165.21 DST=192.168.2.5 LEN=75 TOS=0x00 PREC=0x00 TTL=54 ID=59180 DF PROTO=TCP SPT=443 DPT=53926 WINDOW=40 RES=0x00 ACK PSH URGP=0 
[  455.480903] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=173.192.76.132 DST=192.168.2.5 LEN=264 TOS=0x00 PREC=0x00 TTL=52 ID=45605 DF PROTO=TCP SPT=80 DPT=35363 WINDOW=46 RES=0x00 ACK FIN URGP=0 
[  455.754557] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=64.27.101.155 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x00 TTL=239 ID=0 PROTO=TCP SPT=80 DPT=56974 WINDOW=0 RES=0x00 RST URGP=0 
[  458.905222] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=204.11.51.35 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x00 TTL=235 ID=41233 DF PROTO=TCP SPT=80 DPT=39036 WINDOW=6382 RES=0x00 ACK RST URGP=0 
[  465.311553] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=204.11.51.35 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x00 TTL=236 ID=7287 DF PROTO=TCP SPT=80 DPT=39628 WINDOW=4519 RES=0x00 ACK RST URGP=0 
[  471.430878] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=75.126.18.99 DST=192.168.2.5 LEN=264 TOS=0x00 PREC=0x00 TTL=52 ID=12789 DF PROTO=TCP SPT=80 DPT=42499 WINDOW=46 RES=0x00 ACK FIN URGP=0 
[  472.077336] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=75.126.18.100 DST=192.168.2.5 LEN=605 TOS=0x00 PREC=0x00 TTL=53 ID=20933 DF PROTO=TCP SPT=80 DPT=58646 WINDOW=56 RES=0x00 ACK FIN URGP=0 
[  514.579738] wlan0: deauthenticating from 00:22:75:e0:fd:86 by local choice (reason=3)
[  521.208286] wlan0: authenticate with 00:22:75:e0:fd:86 (try 1)
[  521.211662] wlan0: authenticated
[  521.211954] wlan0: associate with 00:22:75:e0:fd:86 (try 1)
[  521.215875] wlan0: RX ReassocResp from 00:22:75:e0:fd:86 (capab=0x411 status=0 aid=1)
[  521.215885] wlan0: associated
[  532.724527] wlan0: no IPv6 routers present
[  567.436701] wlan0: authenticate with 00:22:75:e0:fd:86 (try 1)
[  567.438348] wlan0: authenticated
[  567.438835] wlan0: associate with 00:22:75:e0:fd:86 (try 1)
[  567.444536] wlan0: RX ReassocResp from 00:22:75:e0:fd:86 (capab=0x411 status=0 aid=1)
[  567.444547] wlan0: associated
[  569.070218] wlan0: deauthenticating from 00:22:75:e0:fd:86 by local choice (reason=3)
[  585.414045] wlan0: authenticate with 00:22:75:e0:fd:86 (try 1)
[  585.415685] wlan0: authenticated
[  585.415940] wlan0: associate with 00:22:75:e0:fd:86 (try 1)
[  585.419776] wlan0: RX ReassocResp from 00:22:75:e0:fd:86 (capab=0x411 status=0 aid=1)
[  585.419784] wlan0: associated
[  596.777534] wlan0: no IPv6 routers present
[  620.167935] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=173.192.76.132 DST=192.168.2.5 LEN=677 TOS=0x00 PREC=0x00 TTL=53 ID=41510 DF PROTO=TCP SPT=80 DPT=35372 WINDOW=58 RES=0x00 ACK PSH URGP=0 
[  642.778008] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=66.220.151.83 DST=192.168.2.5 LEN=158 TOS=0x00 PREC=0x00 TTL=84 ID=35870 DF PROTO=TCP SPT=443 DPT=37854 WINDOW=39 RES=0x00 ACK PSH URGP=0 
[  657.562061] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=75.126.18.100 DST=192.168.2.5 LEN=164 TOS=0x00 PREC=0x00 TTL=53 ID=47860 DF PROTO=TCP SPT=80 DPT=58737 WINDOW=56 RES=0x00 ACK PSH URGP=0 
[  672.367767] [UFW BLOCK] IN=wlan0 OUT= MAC=c4:17:fe:d7:67:3c:00:22:75:e0:fd:86:08:00 SRC=75.126.18.100 DST=192.168.2.5 LEN=164 TOS=0x00 PREC=0x00 TTL=52 ID=5286 DF PROTO=TCP SPT=80 DPT=58738 WINDOW=56 RES=0x00 ACK PSH URGP=0 
[  682.769011] wlan0: deauthenticating from 00:22:75:e0:fd:86 by local choice (reason=3)
[  704.890189] wlan0: authenticate with 80:a1:d7:27:65:d0 (try 1)
[  704.894122] wlan0: authenticated
[  704.898107] wlan0: associate with 80:a1:d7:27:65:d0 (try 1)
[  704.901957] wlan0: RX AssocResp from 80:a1:d7:27:65:d0 (capab=0x411 status=0 aid=3)
[  704.901964] wlan0: associated
[  715.426646] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:80:a1:d7:27:65:d2:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=40162 PROTO=2 
[  716.075000] wlan0: no IPv6 routers present
[  716.273651] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f0:7b:cb:14:32:61:08:00 SRC=192.168.1.6 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=4053 PROTO=2 
[  749.859379] wlan0: deauthenticating from 80:a1:d7:27:65:d0 by local choice (reason=3)
[  752.776676] wlan0: authenticate with 00:22:75:e0:fd:86 (try 1)
[  752.781842] wlan0: authenticated
[  752.786126] wlan0: associate with 00:22:75:e0:fd:86 (try 1)
[  752.789870] wlan0: RX AssocResp from 00:22:75:e0:fd:86 (capab=0x411 status=0 aid=1)
[  752.789880] wlan0: associated
[  763.844495] wlan0: no IPv6 routers present
[  765.456582] wlan0: deauthenticating from 00:22:75:e0:fd:86 by local choice (reason=3)
[  778.272459] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.132408] wlan0: authenticate with 00:22:75:e0:fd:86 (try 1)
[  785.134045] wlan0: authenticated
[  785.134337] wlan0: associate with 00:22:75:e0:fd:86 (try 1)
[  785.138189] wlan0: RX AssocResp from 00:22:75:e0:fd:86 (capab=0x411 status=0 aid=2)
[  785.138199] wlan0: associated
[  785.141338] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  796.027955] wlan0: no IPv6 routers present

------------------------------------------------------------------------------------------------

dmesg | grep -i wireless (No information)

-----------------------------------------------------------------------------------------------

iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Belkin_e0fd86"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:75:E0:FD:86   
          Bit Rate=13 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-86 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:514   Missed beacon:0

----------------------------------------------------------------------------------------------------------------------------------------------

---

### Post by madvinegar on 2012-02-09
I think it must be driver related problem.

Try also this.

Go to synaptics and **uninstall** the 

firmware-b43-installer 

and install in its place the 

firmware-b43legacy-installer.

---

### Post by ganesh3 on 2012-02-09
Hi,

It is still not working. The network has been intermittent and cuts off automatically with the error as before.

Also, for some strange reason 'Synaptics Package Manager' does not load after providing the authentication credentials.

I have been doing all the suggestive steps using Ubuntu Software Center.

My experience is getting stranger by the day.. :(

Regards,

Ganesh Bhat.

---


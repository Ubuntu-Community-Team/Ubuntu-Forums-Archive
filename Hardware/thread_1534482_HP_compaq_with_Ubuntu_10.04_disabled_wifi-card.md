---
title: "HP compaq with Ubuntu 10.04 disabled wifi-card"
date: 2010-07-19
forum: Hardware
---

### Post by Rahmenlos on 2010-07-19
Hi everyone.

One of my Laptops, a HP compaq, is running with Ubuntu 10.04 for a few month now. Yesterday I was trying to configure my microphone for rosetta stone under wine but gave up half way through and just put the laptop into hibernate as usual. Today I'm facing the problem that my wireless card isn't enabled.

I checked if maybe the Wifi-Button is off but no. It lights blue on the button as well as on the indicator led which means Wifi is on. But I can click on the button as much as I want, it won't disable or enable the wifi. it just lights blue and doesn't work at all as a button.

That's what I've done so far:

```
**lspci **
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01) 
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
``````
**ifconfig **
eth0      Link encap:Ethernet  Hardware Adresse 00:1b:38:ef:e7:46   
          inet6-Adresse: fe80::21b:38ff:feef:e746/64 Gültigkeitsbereich:Verbindung 
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1 
          RX packets:1161 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:400115 (400.1 KB)  TX bytes:153595 (153.5 KB) 
          Interrupt:16 Basisadresse:0x1000  
 
lo        Link encap:Lokale Schleife   
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1 
          RX packets:10500 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10500 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0  
          RX bytes:307534 (307.5 KB)  TX bytes:307534 (307.5 KB) 
``````
**ifconfig -a** 
eth0      Link encap:Ethernet  Hardware Adresse 00:1b:38:ef:e7:46   
          inet6-Adresse: fe80::21b:38ff:feef:e746/64 Gültigkeitsbereich:Verbindung 
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1 
          RX packets:1161 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:400115 (400.1 KB)  TX bytes:153595 (153.5 KB) 
          Interrupt:16 Basisadresse:0x1000  
 
lo        Link encap:Lokale Schleife   
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1 
          RX packets:10850 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10850 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0  
          RX bytes:317684 (317.6 KB)  TX bytes:317684 (317.6 KB) 
 
wlan0     Link encap:Ethernet  Hardware Adresse 00:1f:3a:1c:f9:30   
          BROADCAST MULTICAST  MTU:1500  Metrik:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
``````
**iwconfig **
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
``````
**iwlist scan **
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Failed to read scan data : Network is down 
``````
**cat /etc/network/interfaces **
auto lo 
iface lo inet loopback 
``````
**cat /etc/resolv.conf **
# Generated by NetworkManager 
``````
**sudo /etc/init.d/networking restart **
[sudo] password for lilly:  
 * Reconfiguring network interfaces...                                   [ OK ]  
``````
**sudo ifconfig wlan0 up **
SIOCSIFFLAGS: Unknown error 132 
``````
**sudo iwconfig wlan0 txpower** auto, 5, 10, 15  - I tried all 4 entries. nothing.
``````
**rfkill list** 
0: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: yes 
``````
**sudo dhclient wlan0 **
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit https://www.isc.org/software/dhcp/ 
 
SIOCSIFFLAGS: Unknown error 132 
SIOCSIFFLAGS: Unknown error 132 
Listening on LPF/wlan0/00:1f:3a:1c:f9:30 
Sending on   LPF/wlan0/00:1f:3a:1c:f9:30 
Sending on   Socket/fallback 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
send_packet: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
 
```I have no idea left whatsoever. I'd be very happy if anyone could help me. Please. I beg you.

---

### Post by PresenceofMind on 2010-07-19
> **Rahmenlos said:**
> Hi everyone.

One of my Laptops, a HP compaq, is running with Ubuntu 10.04 for a few month now. Yesterday I was trying to configure my microphone for rosetta stone under wine but gave up half way through and just put the laptop into hibernate as usual. Today I'm facing the problem that my wireless card isn't enabled.

I checked if maybe the Wifi-Button is off but no. It lights blue on the button as well as on the indicator led which means Wifi is on. But I can click on the button as much as I want, it won't disable or enable the wifi. it just lights blue and doesn't work at all as a button.

That's what I've done so far:

```
**lspci **
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01) 
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
``````
**ifconfig **
eth0      Link encap:Ethernet  Hardware Adresse 00:1b:38:ef:e7:46   
          inet6-Adresse: fe80::21b:38ff:feef:e746/64 Gültigkeitsbereich:Verbindung 
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1 
          RX packets:1161 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:400115 (400.1 KB)  TX bytes:153595 (153.5 KB) 
          Interrupt:16 Basisadresse:0x1000  
 
lo        Link encap:Lokale Schleife   
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1 
          RX packets:10500 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10500 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0  
          RX bytes:307534 (307.5 KB)  TX bytes:307534 (307.5 KB) 
``````
**ifconfig -a** 
eth0      Link encap:Ethernet  Hardware Adresse 00:1b:38:ef:e7:46   
          inet6-Adresse: fe80::21b:38ff:feef:e746/64 Gültigkeitsbereich:Verbindung 
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1 
          RX packets:1161 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:400115 (400.1 KB)  TX bytes:153595 (153.5 KB) 
          Interrupt:16 Basisadresse:0x1000  
 
lo        Link encap:Lokale Schleife   
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1 
          RX packets:10850 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10850 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0  
          RX bytes:317684 (317.6 KB)  TX bytes:317684 (317.6 KB) 
 
wlan0     Link encap:Ethernet  Hardware Adresse 00:1f:3a:1c:f9:30   
          BROADCAST MULTICAST  MTU:1500  Metrik:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
``````
**iwconfig **
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
``````
**iwlist scan **
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Failed to read scan data : Network is down 
``````
**cat /etc/network/interfaces **
auto lo 
iface lo inet loopback 
``````
**cat /etc/resolv.conf **
# Generated by NetworkManager 
``````
**sudo /etc/init.d/networking restart **
[sudo] password for lilly:  
 * Reconfiguring network interfaces...                                   [ OK ]  
``````
**sudo ifconfig wlan0 up **
SIOCSIFFLAGS: Unknown error 132 
``````
**sudo iwconfig wlan0 txpower** auto, 5, 10, 15  - I tried all 4 entries. nothing.
``````
**rfkill list** 
0: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: yes 
``````
**sudo dhclient wlan0 **
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit https://www.isc.org/software/dhcp/ 
 
SIOCSIFFLAGS: Unknown error 132 
SIOCSIFFLAGS: Unknown error 132 
Listening on LPF/wlan0/00:1f:3a:1c:f9:30 
Sending on   LPF/wlan0/00:1f:3a:1c:f9:30 
Sending on   Socket/fallback 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
send_packet: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
 
```I have no idea left whatsoever. I'd be very happy if anyone could help me. Please. I beg you.

Hey!!!!

I just noticed that your rfkill command gave the answer to your problem. According to it there is a "Hard Block" which is stopping it from starting up the WLAN adapter.

Type this into your command line:

```
rfkill unblock wlan

```That might unblock whatever's blocking it and, hopefully, put you out of your misery.

---

### Post by Rahmenlos on 2010-07-19
Thank you so very much. I unblocked it, restarted and it works now. What a big relieve. Thank you!

---

### Post by PresenceofMind on 2010-07-20
Great!!! 

You're Welcome. Have a nice day.....

---


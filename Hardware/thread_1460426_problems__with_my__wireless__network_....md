---
title: "problems  with my  wireless  network ..."
date: 2010-04-22
forum: Hardware
---

### Post by balki2005 on 2010-04-22
Hello,

I have a very weird problem  with  my  netbook:
my netbook  connects  to  my wireless  networkrouter without problem:
jonay@jonay-laptop:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 90:e6:ba:ed:14:af brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.106/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::92e6:baff:feed:14af/64 scope link 
       valid_lft forever preferred_lft forever
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 1c:4b:d6:2a:c3:4b brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.147/24 brd 192.168.1.255 scope global wlan0
    inet6 fe80::1e4b:d6ff:fe2a:c34b/64 scope link 
       valid_lft forever preferred_lft forever
4: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether 26:15:2d:7f:03:42 brd ff:ff:ff:ff:ff:ff
jonay@jonay-laptop:~$ 

but I have  only a  very short time  internet connection, then is my network connection broken. I mean I am  still  connected  to  my wireless  network, but without  any network connection:

jonay@jonay-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"HERRERA"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:0C:41:9D:5D:ED   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-73 dBm  Noise level=-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

jonay@jonay-laptop:~$ 

but

jonay@jonay-laptop:~$ ping [www.google.com](www.google.com)
^C
jonay@jonay-laptop:~$ mtr  google.com
^C
jonay@jonay-laptop:~$ 

nothing works !!

can somebody  help me  !!!

info  netbook:

System Information
	Manufacturer: MEDION
	Product Name: E121X
	Version: Rev 1.0
	Serial Number: To Be Filled By O.E.M.
	UUID: AC077800-2482-5E0A-D089-90E6BAED14AF
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: To Be Filled By O.E.M.
jonay@jonay-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
jonay@jonay-laptop:~$ 


jonay@jonay-laptop:~$ uname  -a  
Linux jonay-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
jonay@jonay-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid
jonay@jonay-laptop:~$ 

kind regards,

jonay alias  balki2005

---

### Post by nathanhillinbl on 2010-05-05
I'm having the same issue. Wireless is working fine, then all the sudden, the connection stays on, but I have no internet connectivity. Here's my lspci:
```
nate@monte:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260M] (rev a2)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
nate@monte:~$ 

```

Drivers are installed for the Intel 5100 Wireless card, and I didn't have these issues under 9.10. Any help would be GREATLY appreciated, as turning my physical wireless switch on and off again every 5-10 mins is getting REALLY annoying.

Thanks in advance,
Nate

---

### Post by nathanhillinbl on 2010-05-06
Anyone able to help us? It's quite annoying to have to either switch my wireless hard switch on and off, or reboot every 10 mins!

---

### Post by nathanhillinbl on 2010-05-06
I had both wicd and networkmanager running at the same time, and (cross my fingers) think that that's what screwed it up.

---

### Post by joeinbend on 2010-05-07
Guys did that solve the problem for you? i have the same Atheros card in my netbook with similar issues on 10.04 (desktop or netbook remix). Can you describe in detail what you did to fix this?

---

### Post by greenchilli on 2010-05-07
I've never had issues before, well, maybe every time I upgrade. Upgraded yesterday to Lucid and tested at home - Wireless network detected and then it disappeared from the network config screen. 
I'm gonna try the solutions from the following forum:

[http://ubuntuforums.org/showthread.php?t=1476019](http://ubuntuforums.org/showthread.php?t=1476019)

try it out and let us know.

---


---
title: "No available wifi connections."
date: 2009-12-18
forum: Hardware
---

### Post by raijinnathan on 2009-12-18
Hi. when i was in manila, i usually use my globe tatoo to connect to the internet. And my laptop (MSI EX460) was also able to detect a wireless connection of our neighbour[B].
[/B]
But when i got home in our province, my laptop cannot even detect my own wifi. i am running a TP-LINK wifi in our home, with WPA as the security. i installed Rutilt WAN manager and even network-config so that i could scan my wifi, but to no avail.

running network-config, i  have:

Configuring device wlan0 :

$ iwconfig wlan0 mode managed

$ iwconfig wlan0 essid "TP-LINK_C242FC"

$ iwconfig wlan0 rate auto

$ iwconfig wlan0 key off

$ pkill wpa_supplicant

$ wpa_supplicant -B -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant/wpa_psk.conf
Unsupported driver 'ndiswrapper'.

$ ifconfig wlan0 up

DHCP may take a while, please wait...
$ dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5103
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:24:21:c6:63:54
Sending on   LPF/wlan0/00:24:21:c6:63:54
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Configuring device wlan0:avahi :
$ ifconfig wlan0:avahi down
Configuring device eth0 :
$ ifconfig eth0 up
DHCP may take a while, please wait...
$ dhclient eth0


running iwconfig, i have:
raijinnathan@raijinnathan-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


lspci had the following output:
raijinnathan@raijinnathan-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
raijinnathan@raijinnathan-laptop:~$ 

hope somebody can help.

i am running ubuntu 9.10. TIA :)

_______________________________________________

scratch this one. my wifi is running smoothly now. :)

---


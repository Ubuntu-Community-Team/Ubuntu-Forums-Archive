---
title: "Wireless no longer working"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by Hatty on 2009-02-01
I have just upgraded to 8.10 Intrepid Ibex. The updates completed, the computer restarted, and wireless no longer works.

NetworkManager refuses to manage my wireless device, so I have resorted to the console, but that doesn't work either.
> root@sakura:~# ifup wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0c:41:58:58:4b
Sending on   LPF/wlan0/00:0c:41:58:58:4b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.

[quote="lshw"]  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:58:58:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.0-86 wireless=IEEE 802.11b
[/quote]

> root@sakura:~# iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"gerryhome"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:F0:70:33:30   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Encryption key:off
          Power Management:off
          Link Quality=78/100  Signal level=78/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



As you can see, it does in fact SEE the wireless network, but refuses to connect. I had no problem with this prior to upgrading to Ibex.

Any helpw ould be much appreciated.

---

### Post by geroad on 2009-02-10
> **Hatty said:**
> I have just upgraded to 8.10 Intrepid Ibex. The updates completed, the computer restarted, and wireless no longer works.

NetworkManager refuses to manage my wireless device, so I have resorted to the console, but that doesn't work either.






As you can see, it does in fact SEE the wireless network, but refuses to connect. I had no problem with this prior to upgrading to Ibex.

Any helpw ould be much appreciated.
There have been a lot of problems with "Network Manager". I now use 
"Wifi-radar".  Its available in the Add/Remove Application and
Synaptic Package Manager.

---

### Post by Neural oD on 2009-02-10
in the terminal - make sure that your wired connection is down: sudo ifdown eth0
then: sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "whatever it is - without quotes"
sudo iwconfig wlan0 channel "put your channel here"
sudo ifconfig wlan0 up
sudo dhclient wlan0


that should do the trick for you

---

### Post by Neural oD on 2009-02-10
You also might want to kill the NetworkManager process - as this could interfere

---

### Post by jsacks on 2009-02-11
Same problem but the solutions are not working for me.... the wifi radar doesnt work either

jared@dell-desktop:~$ sudo ifdown eth0
[sudo] password for jared: 
ifdown: interface eth0 not configured
jared@dell-desktop:~$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
jared@dell-desktop:~$ sudo iwconfig wlan0 essid 00300AA0DFAE
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
jared@dell-desktop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
jared@dell-desktop:~$ 
jared@dell-desktop:~$

---


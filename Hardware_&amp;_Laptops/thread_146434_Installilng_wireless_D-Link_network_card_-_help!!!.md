---
title: "Installilng wireless D-Link network card - help!!!"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by Roxxor on 2006-03-18
I am new to Ubuntu. I installed it today. It´s on a Laptop. I have a wirelss D-Link DWL-G650 network card and I don´t know how to install the drivers and configure the card. 

I just downloaded and installed  *ndiswrapper* and I also have the drivers for the card. 

So how do I go on?

---

### Post by NoWhereMan on 2006-03-18
[QUOTE=Roxxor]So how do I go on?[/QUOTE]

looking here? [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by Roxxor on 2006-03-18
Ok, now I have a **wlan0** interface and I have typed the correct SSID (Network name) and WEP. And I am using ASCII (as the router configuration) but I can still not connect. It says the connection is active, but I still get no IP-number. 

What´s wrong?

```

ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:80:C8:12:AA:59
          inet6 addr: fe80::280:c8ff:fe12:aa59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:316979 (309.5 KiB)  TX bytes:0 (0.0 b)
          Memory:d0100000-d010ffff

```


PLEASE, HELP ME!!!

---

### Post by firecat53 on 2006-03-18
Did you do 
```
sudo dhclient wlan0
```
yet?

What's the output of iwconfig?

Scott

---

### Post by Roxxor on 2006-03-19
My computer (network card) detects the network but it does not connect to it. I have typed the correct WEP key.
Our router is set to:
- Channel 1
- Open System 
- Ascii
- 64 bit encryption

sudo dhclient wlan0
```

roxxor@laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:80:c8:12:aa:59
Sending on   LPF/wlan0/00:80:c8:12:aa:59
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

ndiswrapper -l
```

roxxor@laptop:~$ ndiswrapper -l
Installed ndis drivers:
net5211 driver present, hardware present

```

ifconfig
```

roxxor@laptop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:540657 (527.9 KiB)  TX bytes:540657 (527.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:C8:12:AA:59
          inet6 addr: fe80::280:c8ff:fe12:aa59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66834 (65.2 KiB)  TX bytes:0 (0.0 b)
          Memory:d0100000-d010ffff
```
iwconfig
```
roxxor@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"OurNetwork"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:108 Mb/s
          Link Quality:61/100  Signal level:-34 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

#iface ath0 inet dhcp
#wireless-essid OurNetwork
#wireless-key s:XXXXX

#auto ath0



iface wlan0 inet dhcp
wireless yes
wireless-mode managed
wireless-essid OurNetwork
wireless-key s:XXXXX


iface eth0 inet dhcp

auto eth0
```


I have done everything I know. :cry:

---

### Post by thomas.hood on 2006-03-23
Same problem for me:
[http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=840106](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=840106)

Anyone?

Tom

---


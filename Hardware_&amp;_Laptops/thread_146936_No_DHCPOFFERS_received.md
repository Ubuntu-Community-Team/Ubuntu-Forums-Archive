---
title: "No DHCPOFFERS received"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by thomas.hood on 2006-03-19
I followed the how-to on installing ndiswrapper and appartently it installed correctly: I can see my router and my neighbours in the Network setttings gui.
However, I don't seem to be getting a connection to the router. The network has no encryption and there are no other network cards present on the system. It seems to fail when getting an ip address (see below)

The card is a Belkin f5d8010 Pre N with matching router (it works fine under windows)

Any ideas?

Thanks,

Tom

tom@inspiron:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

wlan0     Auto  ESSID:"hoodswifi2"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:50:29:6F:FE
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:45/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tom@inspiron:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2635727 (2.5 MiB)  TX bytes:2635727 (2.5 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:29:D3:BE
          inet6 addr: fe80::211:50ff:fe29:d3be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:88924 (86.8 KiB)  TX bytes:38826 (37.9 KiB)
          Memory:15000000-1507ffff

tom@inspiron:~$ dhcpclient
bash: dhcpclient: command not found
tom@inspiron:~$ dhcpdclient
bash: dhcpdclient: command not found
tom@inspiron:~$ dhclient
There is already a pid file /var/run/dhclient.pid with pid 8570
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
tom@inspiron:~$ sudo dhclient
Password:
There is already a pid file /var/run/dhclient.pid with pid 8570
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:11:50:29:d3:be
Sending on   LPF/wlan0/00:11:50:29:d3:be
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
bogus UDP packet length: 556
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
bogus UDP packet length: 556
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 12
bogus UDP packet length: 556
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 12
bogus UDP packet length: 556
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
bogus UDP packet length: 556
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
bogus UDP packet length: 556
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 5
bogus UDP packet length: 556
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

tom@inspiron:~$ ndiswrapper -l
Installed ndis drivers:
netani  driver present, hardware present

tom@inspiron:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:29:6F:FE
                    ESSID:"hoodswifi2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-45 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0F:66:87:4E:C6
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-44 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
tom@inspiron:~$

---

### Post by thomas.hood on 2006-03-23
Searching the forums it appears I'm not the only one who has this problem, and I see no resolutions for it...

[http://www.ubuntuforums.org/showthread.php?t=146434&highlight=DHCPOffers+776](http://www.ubuntuforums.org/showthread.php?t=146434&highlight=DHCPOffers+776)

[http://www.ubuntuforums.org/showthread.php?t=85779&highlight=DHCPOffers+776](http://www.ubuntuforums.org/showthread.php?t=85779&highlight=DHCPOffers+776)

[http://www.ubuntuforums.org/showthread.php?t=142498&highlight=DHCPOffers+776](http://www.ubuntuforums.org/showthread.php?t=142498&highlight=DHCPOffers+776)

[http://www.ubuntuforums.org/showthread.php?t=139889&highlight=DHCPOffers+776](http://www.ubuntuforums.org/showthread.php?t=139889&highlight=DHCPOffers+776)

[http://www.ubuntuforums.org/showthread.php?t=137806&highlight=DHCPOffers+776](http://www.ubuntuforums.org/showthread.php?t=137806&highlight=DHCPOffers+776)

and so on.

One possible solution is:
[http://www.ubuntuforums.org/showthread.php?t=137838&page=2&highlight=DHCPOffers+776](http://www.ubuntuforums.org/showthread.php?t=137838&page=2&highlight=DHCPOffers+776)

"Change the host name -- either in Windows or Ubuntu -- to match one another. Then the DSL connection will think it's still talking to the same machine and all will be well.

What a simple solution to a vexing problem!

In Ubunutu: System/Administrator/Networking/General/Host name
In Windows: Control Panel/System/Network Properties/Computer name"

Which isn't a option as the Ubuntu screwed my xp installation :evil: !!!

Anyone?

Thanks,

Tom

---

### Post by thomas.hood on 2006-03-29
I reinstalled windows (yes that's how frustrating this is) and tried the 'fix' which -- you guessed it --  did sweet fa.

There really are a very large number of people with _exactly_ the same problem as me. Do a search for "DHCPOFFERS" -- there's a new problem reported with these symptoms nearly every day.

Can someone else recommend another distro that's similarly easy to install, but has functioning networking?

Tpom

---


---
title: "Can not connect to wireless (wi-fi) network."
date: 2010-07-13
forum: Hardware
---

### Post by sarin20 on 2010-07-13
Hello, dear community!

I have Dell vostro 1015 laptop with Ubuntu 10.04. Few days ago I got wi-fi router and now try to connect my laptop to my wi-fi network. Network was created succesfully, my smartphone found it and I can go to the Web with it. But laptop did not connects.

iwlist scan found my network:

[FONT="Courier New"]root@dell-desktop:/home/sarin# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:49:C9:C2:0C
                    ESSID:"ZyXEL"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 48:5B:39:BB:D7:67
                    ESSID:"sarin"
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:5/5  Signal level:-24 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s[/FONT]

iwconfig succesfully set ESSID and other parameters (only by essid it set frequency and Access point!):

[FONT="Courier New"]root@dell-desktop:/home/sarin# iwconfig eth1 essid sarin
root@dell-desktop:/home/sarin# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"sarin"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 48:5B:39:BB:D7:67   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-23 dBm  Noise level=-65 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/FONT]

after it I was stoped the eth0 interface (Ethernet), start eth1 (wi-fi) and try dhclient:
[FONT="Courier New"]root@dell-desktop:/home/sarin# ifconfig eth1 up                                                     
root@dell-desktop:/home/sarin# dhclient eth1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/70:1a:04:37:86:11
Sending on   LPF/eth1/70:1a:04:37:86:11
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/FONT]

But network does not works.

I think that problem in dhclient, but I am noob in wi-fi and not profi in Linux.

Thanks!

PS: for example: dhclient for eth0:
[FONT="Courier New"]
root@dell-desktop:/home/sarin# dhclient eth0                                                      
There is already a pid file /var/run/dhclient.pid with pid 3764
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:26:b9:0d:75:1f
Sending on   LPF/eth0/00:26:b9:0d:75:1f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 38431 seconds.
[/FONT]

---


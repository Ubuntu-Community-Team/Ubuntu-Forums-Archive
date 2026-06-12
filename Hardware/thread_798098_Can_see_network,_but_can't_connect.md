---
title: "Can see network, but can't connect"
date: 2008-05-17
forum: Hardware
---

### Post by new2linux2008 on 2008-05-17
I Thought it would be best to show you what I mean.
I turned all security off. I've also tried with security on and also with setting the freq. channel as well as setting the IP manual, it will say it's connected, but it won't be.

Here is a pic of my setup:
[IMG]http://a499.ac-images.myspacecdn.com/images01/36/l_f238faba562617fb2c804b01c6b268aa.jpg[/IMG]

Here it is searching for ip:
[IMG]http://a505.ac-images.myspacecdn.com/images01/46/l_0058d7b99323a4534f327fbbbf8b35c0.jpg[/IMG]

Here is what I end up with:
[IMG]http://a667.ac-images.myspacecdn.com/images01/44/l_d2f409cc4b8527b2335aa012b2a92d82.jpg[/IMG]

---

### Post by teaker1s on 2008-05-17
had similar issue with orange live box, have you tried another wireless access point (a public or friends maybe)

---

### Post by new2linux2008 on 2008-05-19
other networks didn't work either. if I aren't able to get this working with ubuntu I'm probably about to switch back to vistia

---

### Post by unutbu on 2008-05-19
Well, I'm not great at solving networking issues, but I'll take a swing. To start, please open a terminal (Applications>Accessories>Terminal) and post the output to the following commands:

```
ifconfig
iwconfig
iwlist scan
route
sudo /etc/init.d/networking restart

```

---

### Post by new2linux2008 on 2008-05-20
**ifconfig**=


eth0      Link encap : Ethernet  HWaddr 00 : 1b : 24:fa:30 : 3a  
          UP BROADCAST MULTICAST  MTU: 1500  Metric: 1
          RX packets: 3857 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets: 3747 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 txqueuelen: 1000 
          RX bytes: 3310914 (3.1 MB)  TX bytes: 521364 (509.1 KB)
          Interrupt: 252 Base address: 0xa000 

lo        Link encap: Local Loopback  
          inet addr: 127.0.0.1  Mask: 255.0.0.0
          inet6 addr: :: 1/128 Scope: Host
          UP LOOPBACK RUNNING  MTU: 16436  Metric: 1
          RX packets: 12048 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets: 12048 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 txqueuelen: 0 
          RX bytes:684589 (668.5 KB)  TX bytes:684589 (668.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:7a:cc:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped: 0 overruns: 0 frame: 0
          TX packets:141 errors:0 dropped:5 overruns: 0 carrier: 0
          collisions:0 txqueuelen:1000 
          RX bytes:180 (180.0 B)  TX bytes:14297 (13.9 KB)
          Interrupt:19 Memory:f6000000-f6010000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1e:4c:7a:cc:ab  
          inet addr:169.254.8.172  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f6000000-f6010000

---

### Post by new2linux2008 on 2008-05-20
**iwconfig**=

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  Nickname:"linksys"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management: off
          Link Quality: 0  Signal level:0  Noise level:0
          Rx invalid nwid: 0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon:0

---

### Post by new2linux2008 on 2008-05-20
**iwlist scan** =
 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

          Cell 01 - Address: 00: 1C: 10: B0: BF: DE
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-14 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

          Cell 02 - Address: 00: 17: 3F: A6: 3F: 9F
                    ESSID:"JoNJen"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

          Cell 03 - Address: 00: 18: 3F: 6C: DE: 91
                    ESSID:"2WIRE900"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

          Cell 04 - Address: 00: 1D: 7E: 3B: B4: D5
                    ESSID:"b3hrden"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

          Cell 05 - Address: 00: 17: 3F: 65: 57: 66
                    ESSID:"IPMaha2/"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by new2linux2008 on 2008-05-20
**route**=

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 wlan0
default         *               0.0.0.0         U     1000   0        0 wlan0

---

### Post by new2linux2008 on 2008-05-20
**sudo /etc/init.d/networking restart**  =
 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 8375
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by new2linux2008 on 2008-05-20
hope this info is helpfull. Took me a bit to post a replay b/c the forum gave me a error each time I tried to post all of it together. oh well, there's the info. Also, side note is : I Tried to connect to my router again and it would say connected to : my router but wouldn't obtain a ip address then would say connected to: none. once it realized there was no ip, using wifi radar

---

### Post by unutbu on 2008-05-20
It looks like you've turned off all security (WPA) on your wireless card, but it looks like security is "on" on the router:

```
Cell 01 - Address: 00: 1C: 10: B0: BF: DE
ESSID:"linksys"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:100/100 Signal level:-14 dBm Noise level:-96 dBm
**Encryption key: on**
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
12 Mb/s; 48 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: WPA Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
```

Just to get a working connection, turn off security on the router temporarily. We can work on getting WPA working after you know you can establish a connection.

---

### Post by new2linux2008 on 2008-05-20
I've turned it off

          Cell 01 - Address: 00:1C:10:B0:BF:DE
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-23 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

---

### Post by unutbu on 2008-05-20
Okay, great. Now try

```
sudo /etc/init.d/networking restart
```
again. If it doesn't work, reboot and see if you can get a connection with WiFi Radar. If that doesn't work try the 'restart' command again. If still no joy, please post the output.

---

### Post by new2linux2008 on 2008-05-20
$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 4636
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.102 from 192.168.1.1
DHCPREQUEST of 192.168.1.102 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.102 from 192.168.1.1
bound to 192.168.1.102 -- renewal in 33200 seconds.

---

### Post by new2linux2008 on 2008-05-20
previous was while connected via cat 5 . not sure if that matters

---

### Post by new2linux2008 on 2008-05-20
it worked. omg you are a god

---

### Post by unutbu on 2008-05-20
Fantastic. Now to get WPA working, I would try

[Kevdog's excellent guide]("http://ubuntuforums.org/showthread.php?t=684495"). Go to the "WPA Connection" section.

One small caveat: It's better not to mix apt tools (apt-get/Synaptic/Adept) with aptitude, so if you aren't an aptitude user, I suggest you run 

```
sudo apt-get install wpasupplicant
```

instead of 

```
sudo aptitude install wpasupplicant
```
(The issue here is that if you mix apt-get and aptitude, one will not remove packages the other installed. So if you every decide to uninstall a package, you'd have to remember which package manager you had used before...)

Anyway, his instructions are pretty straight-forward. Good luck!

---

### Post by new2linux2008 on 2008-05-24
ok, back to bad news. it's now not working again. I restarted then problems came back. i tried running the ezact same commands but couldn't get it to work

---

### Post by new2linux2008 on 2008-05-24
iwconfig =

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"@home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00: 11: 50: A5: C0: 56   
          Bit Rate=54 Mb/s   
          Power Management: off
          Link Quality: 100/100  Signal level: -27 dBm  Noise level: -96 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 8  Invalid misc: 6200   Missed beacon: 0

---

### Post by new2linux2008 on 2008-05-24
ifonfig = 
eth0      Link encap:Et  hernet  HWaddr 00: 1b: 24: fa: 30: 3a  
          inet addr:192.168.2.5  Bcast: 192.168.2.255  Mask: 255.255.255.0
          inet6 addr: fe80:: 21b: 24ff: fefa: 303a/64 Scope: Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1578220 (1.5 MB)  TX bytes:233740 (228.2 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap: Local Loopback  
          inet addr: 127.0.0.1  Mask: 255.0.0.0
          inet6 addr: :: 1/128 Scope: Host
          UP LOOPBACK RUNNING  MTU: 16436  Metric: 1
          RX packets: 247 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets: 247 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 txqueuelen: 0 
          RX bytes:14968 (14.6 KB)  TX bytes:14968 (14.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00: 1e: 4c: 7a: cc: ab  
          inet6 addr: fe80::21e:4cff:fe7a:ccab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets: 74 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets: 158 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 txqueuelen: 1000 
          RX bytes: 7448 (7.2 KB)  TX bytes:20010 (19.5 KB)
          Interrupt: 19 Memory:f6000000-f6010000 

wlan0: avahi Link encap: Ethernet  HWaddr 00: 1e: 4c: 7a: cc: ab  
          inet addr: 169.254.8.172  Bcast: 169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:f6000000-f6010000

---

### Post by new2linux2008 on 2008-05-24
route =
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    100    0        0 eth0
default         *               0.0.0.0         U     1000   0        0 wlan0

---

### Post by new2linux2008 on 2008-05-24
iwlist scan =

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00: 11: 50: A5: C0: 56
                    ESSID: "@home"
                    Protocol: IEEE 802.11g
                    Mode: Managed
                    Frequency: 2.437 GHz (Channel 6)
                    Quality: 100/100  Signal level: -29 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra: bcn_int=100
                    Extra: atim=0

---

### Post by new2linux2008 on 2008-05-24
sudo /etc/init.d/networking restart = 

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6610
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:24:fa:30:3a
Sending on   LPF/eth0/00:1b:24:fa:30:3a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6686
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:24:fa:30:3a
Sending on   LPF/eth0/00:1b:24:fa:30:3a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.2.5 from 192.168.2.1
DHCPREQUEST of 192.168.2.5 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.5 from 192.168.2.1
bound to 192.168.2.5 -- renewal in 2147483648 seconds.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00: 1e:4c:7a:cc:ab
Sending on   LPF/wlan0/00: 1e:4c:7a:cc:ab
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by unutbu on 2008-05-25
It appears your router has changed: Your latest `iwlist scan` reports

```
wlan0 Scan completed :
Cell 01 - Address: [B]00: 11: 50: A5: C0: 56
[/B]ESSID: "@home"
```

whereas before it was

```
Cell 01 - Address: **00: 1C: 10: B0: BF: DE**
ESSID:"linksys"

```

When you change routers, you have to go back and look at the router settings. For example, you are using DHCP. Make sure your new router has DHCP turned on.

---

### Post by new2linux2008 on 2008-05-25
ok true, I'm at a friends house now so that's the reason for the network name change. I'll do the same commands without being connected and show results

---

### Post by new2linux2008 on 2008-05-25
sudo /etc/init.d/networking restart =

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5878
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:24:fa:30:3a
Sending on   LPF/eth0/00:1b:24:fa:30:3a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5930
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:24:fa:30:3a
Sending on   LPF/eth0/00:1b:24:fa:30:3a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   LPF/wlan0/00:1e:4c:7a:cc:ab
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by new2linux2008 on 2008-05-25
route =
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 wlan0
default         *               0.0.0.0         U     1000   0        0 eth0

---

### Post by new2linux2008 on 2008-05-25
iwlist scan =
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:A5:C0:56
                    ESSID:"@home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by new2linux2008 on 2008-05-25
iwconfig =
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"@home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:A5:C0:56   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:1316   Missed beacon:0

---

### Post by new2linux2008 on 2008-05-25
tried it not connected. there was my results

---

### Post by new2linux2008 on 2008-05-25
i got it to work like twice on my home network but no clue why it's not working anymore

---

### Post by new2linux2008 on 2008-05-25
i'm thinking about putting vista back on and dual booting b/c my wireless is really pissing me the **** off. please HELP!!!

---

### Post by unutbu on 2008-05-25
Sorry new2linux2008, you've reached the end of my knowledge. I've looked at your output from ifconfig, iwconfig, iwlist scan and /etc/init.d/networking restart, and from what I see you are getting stuck on the step where the router is supposed to give you an IP address via DHCP.

```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
**No DHCPOFFERS received.**
No working leases in persistent database - sleeping.
```

This sometimes happens to me and my unhappy solution is simply to reboot. Don't blame linux, blame the wifi manufacturers who won't disclose enough information for linux developers to write native drivers. 

Although it's crude, rebooting works for me because the settings on my machine and on my router are in sync. All I can suggest to you is to double check your settings in Wifi radar and your settings on your router. Fiddling with settings on Wifi radar and your router may be a good idea -- just be sure you make notes on what your current settings are and what changes you make so you can return to your current setup as need be.

I feel you are very close to having a working network connection on both networks. Obtaining the DHCP lease is (just about) the very last step.
If you have some patience I think you'll find a way to make it work.

Sorry I can't be of more help; good luck.

---

### Post by new2linux2008 on 2008-05-25
I don't blame linux. I was actully trying to get my friends to convert to linux. I just it would have worked. I don't know how it happened but it did once work. humm.. oh well... back to vista and dual booting

---


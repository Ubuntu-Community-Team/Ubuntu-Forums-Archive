---
title: "Hardy install - can't enter valid wep key"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by JerryI on 2009-03-13
Installing Hardy and cannot access network 2wire411 although the computer "sees" several networks in the vicinity including the target network.  wep key 0360663701 is rejected. The wep key works from XP on this dual-boot computer and from Intrepid or Vista on another dual-boot computer and from XP on a third computer attached to the same network. The following may provide a hint, but is beyond my level of expertise.

------------------------------------------------------------------------ 
jerry@laptop:~$ sudo iwconfig 
[sudo] password for jerry: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Encryption key:off
          Link Quality=48/100  Signal level=41/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jerry@laptop:~$ 

jerry@laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Encryption key:off
          Link Quality=71/100  Signal level=40/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jerry@laptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:22:A4:1C:BD:B1
                    ESSID:"2WIRE411"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 348ms ago
          Cell 02 - Address: 00:14:95:87:6D:B1
                    ESSID:"2WIRE675"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    Extra: Last beacon: 240ms ago
          Cell 03 - Address: 00:1D:7E:C5:69:8B
                    ESSID:"supreme"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=11/100  
                    Extra: Last beacon: 280ms ago

jerry@laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1e:37:f6:cc:c4
Sending on   LPF/eth1/00:1e:37:f6:cc:c4
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jerry@laptop:~$

---


---
title: "Wireless Network not showing in Connection Properties"
date: 2010-01-05
forum: Hardware
---

### Post by hersche1 on 2010-01-05
Background:


Toshiba Tecra M1 with Jaunty Jackalope


Intel Pro/Wireless Lan 2100 driver is installed through NDISWrapper 
(file: w70n51.inf, there is a sys file, I did copied into the driver folder)


[LIST]
[*] Driver: w70n51.inf [http://newsjpl.free.fr/linux/nx7000/rpm/w70n51.inf](http://newsjpl.free.fr/linux/nx7000/rpm/w70n51.inf)
[*] Driver: w70n51.sys [http://newsjpl.free.fr/linux/nx7000/rpm/w70n51.sys](http://newsjpl.free.fr/linux/nx7000/rpm/w70n51.sys)
[/LIST]
 **[B]*[SIZE=1]Source: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Intel_PRO/Wireless_2100_3A](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Intel_PRO/Wireless_2100_3A)[/SIZE]***

[/B] I did get an error: "Unable to see if hardware is present", in any case I installed the driver above and ran the scan from terminal and it seems the wireless lan card is seeing the broadcast from my wireless network. But I can log onto it because it does not present itself in the Network Connection, only the ethenet, eth0 is found.

Please help this newbie to the world of Ubuntu and Linux.

I am having fun, but would have more fun configuring this laptop with wireless for my father in-law.


Terminal screen data:

       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter



wlan0     Link encap:Ethernet  HWaddr 00:04:23:5a:fd:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:dfddf000-dfde0000 



wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:7E:92:EA
                    ESSID:"chuck-1"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---


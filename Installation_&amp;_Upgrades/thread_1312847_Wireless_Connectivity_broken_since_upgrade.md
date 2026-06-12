---
title: "Wireless Connectivity broken since upgrade"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by bergfly on 2009-11-03
I have just upgraded my primary work laptop from 9.04 with lots of ppa's to 9.10. It was not at all smooth, although given the modifications to the system I am not going to blame the upgrader. However, once I finally got it up and running, I have been unable to connect to my wireless AP at work. This worked well in 9.04, but has failed now. The wireless card works fine as I can connect at home without issue. We have a hidden SSID at work on a Cisco AP, using WPA2. I previously pulled out the Kubuntu network manager and installed wicd as the last network manager was clearly broken (could not access a hidden SSID). I am running Kubuntu 9.10 on an Intel Pro adaptor and have tired both the network manager and wicd.

Given the issue I brought in my dell netbook. It has a broadcom adaptor with a Vanilla install from ISO of Ubuntu 9.10. It also works at home but is unable to connect at work. 

Since I am trying to promote getting some Linux machines into the office here, I need this to work. I could simply downgrade them to 9.04, but would prefer to have 9.10 working. Any ideas where to start on getting this sorted?

---

### Post by bergfly on 2009-11-04
Any one had similar issues? I have disabled IPV6 in case that was an issue (it certainly slowed up browsing) Still no luck.

---

### Post by Batzi on 2009-11-04
> **bergfly said:**
> Any one had similar issues? I have disabled IPV6 in case that was an issue (it certainly slowed up browsing) Still no luck.

You're lucky because ever since I upgraded to 9.10 I couldn't connect to the internet at all.

---

### Post by bergfly on 2009-11-04
I have been trying a couple things in wicd backend with no luck. When it works this is what I get in the wicd.log with debug on

> 2009/11/02 21:12:02 :: Autoconnecting...
2009/11/02 21:12:02 :: ifconfig eth0 up
2009/11/02 21:12:07 :: Starting wireless autoconnect...
2009/11/02 21:12:07 :: No wired connection present, attempting to autoconnect to wireless network
2009/11/02 21:12:07 :: scanning start
2009/11/02 21:12:07 :: ifconfig wlan0 up
2009/11/02 21:12:07 :: iwlist wlan0 scan
2009/11/02 21:12:09 :: scanning done
2009/11/02 21:12:09 :: found 8 networks:
2009/11/02 21:12:09 :: found afterscript in configuration None
2009/11/02 21:12:09 :: found ip in configuration None
2009/11/02 21:12:09 :: found netmask in configuration None
2009/11/02 21:12:09 :: found key in configuration oreobutterjava
2009/11/02 21:12:09 :: found gateway in configuration None
2009/11/02 21:12:09 :: found use_global_dns in configuration 0
2009/11/02 21:12:09 :: found disconnect in configuration None
2009/11/02 21:12:09 :: found dns3 in configuration None
2009/11/02 21:12:09 :: found dns1 in configuration None
2009/11/02 21:12:09 :: found use_settings_globally in configuration 0
2009/11/02 21:12:09 :: found use_static_dns in configuration 0
2009/11/02 21:12:09 :: found dns2 in configuration None
2009/11/02 21:12:09 :: found beforescript in configuration None
2009/11/02 21:12:09 :: found enctype in configuration wpa
2009/11/02 21:12:09 :: found automatic in configuration True
2009/11/02 21:12:09 :: stfnet has profile
2009/11/02 21:12:09 :: trying to automatically connect to...stfnet
2009/11/02 21:12:09 :: Connecting to wireless network stfnet
2009/11/02 21:12:09 :: /sbin/dhclient -r eth0
2009/11/02 21:12:09 :: ifconfig eth0 0.0.0.0 
2009/11/02 21:12:09 :: /sbin/ip route flush dev eth0
2009/11/02 21:12:09 :: ifconfig eth0 down
2009/11/02 21:12:09 :: ifconfig eth0 up
2009/11/02 21:12:09 :: Putting interface down
2009/11/02 21:12:09 :: ifconfig wlan0 down
2009/11/02 21:12:09 :: Releasing DHCP leases...
2009/11/02 21:12:09 :: /sbin/dhclient -r wlan0
2009/11/02 21:12:10 :: Setting false IP...
2009/11/02 21:12:10 :: ifconfig wlan0 0.0.0.0 
2009/11/02 21:12:10 :: Stopping wpa_supplicant
2009/11/02 21:12:10 :: wpa_cli -i wlan0 terminate
2009/11/02 21:12:10 :: Flushing the routing table...
2009/11/02 21:12:10 :: /sbin/ip route flush dev wlan0
2009/11/02 21:12:10 :: iwconfig wlan0 mode managed
2009/11/02 21:12:10 :: Putting interface up...
2009/11/02 21:12:10 :: ifconfig wlan0 up
2009/11/02 21:12:10 :: enctype is wpa
2009/11/02 21:12:10 :: Generating psk...
2009/11/02 21:12:10 :: ['/usr/bin/wpa_passphrase', 'stfnet', 'oreobutterjava']
2009/11/02 21:12:10 :: Attempting to authenticate...
2009/11/02 21:12:10 :: ['wpa_supplicant', '-B', '-i', 'wlan0', '-c', '/var/lib/wicd/configurations/0021299b34d8', '-D', 'wext']
2009/11/02 21:12:10 :: ['iwconfig', 'wlan0', 'essid', 'stfnet']
2009/11/02 21:12:10 :: iwconfig wlan0 channel 11
2009/11/02 21:12:10 :: iwconfig wlan0 ap 00:21:29:9B:34:D8
2009/11/02 21:12:10 :: WPA_CLI RESULT IS DISCONNECTED
2009/11/02 21:12:11 :: WPA_CLI RESULT IS ASSOCIATING
2009/11/02 21:12:12 :: WPA_CLI RESULT IS COMPLETED
2009/11/02 21:12:12 :: Running DHCP
2009/11/02 21:12:12 :: /sbin/dhclient wlan0
2009/11/02 21:12:12 :: Internet Systems Consortium DHCP Client V3.1.2
2009/11/02 21:12:12 :: Copyright 2004-2008 Internet Systems Consortium.
2009/11/02 21:12:12 :: All rights reserved.
2009/11/02 21:12:12 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2009/11/02 21:12:12 :: 
2009/11/02 21:12:13 :: Listening on LPF/wlan0/00:1f:3b:5b:04:dd
2009/11/02 21:12:13 :: Sending on   LPF/wlan0/00:1f:3b:5b:04:dd
2009/11/02 21:12:13 :: Sending on   Socket/fallback
2009/11/02 21:12:17 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
2009/11/02 21:12:18 :: DHCPOFFER of 192.168.10.102 from 192.168.10.10
2009/11/02 21:12:18 :: DHCPREQUEST of 192.168.10.102 on wlan0 to 255.255.255.255 port 67
2009/11/02 21:12:18 :: DHCPACK of 192.168.10.102 from 192.168.10.10
2009/11/02 21:12:18 :: bound to 192.168.10.102 -- renewal in 41720 seconds.
2009/11/02 21:12:18 :: DHCP connection successful
2009/11/02 21:12:18 :: Connecting thread exiting.
2009/11/02 21:12:18 :: IP Address is: 192.168.10.102
2009/11/02 21:12:19 :: Sending connection attempt result Success


When I attempt to do this at work, I get this

> 2009/11/04 11:42:40 :: iwconfig wlan0
2009/11/04 11:44:08 :: Autoconnecting...
2009/11/04 11:44:08 :: Starting wireless autoconnect...
2009/11/04 11:44:08 :: No wired connection present, attempting to autoconnect to wireless network
2009/11/04 11:44:08 :: scanning start
2009/11/04 11:44:08 :: ifconfig wlan0 up
2009/11/04 11:44:08 :: iwlist wlan0 scan
2009/11/04 11:44:09 :: hidden
2009/11/04 11:44:09 :: hidden
2009/11/04 11:44:09 :: hidden
2009/11/04 11:44:09 :: hidden
2009/11/04 11:44:09 :: scanning done
2009/11/04 11:44:09 :: found 9 networks:
2009/11/04 11:44:09 :: found afterscript in configuration None
2009/11/04 11:44:09 :: found postdisconnectscript in configuration None
2009/11/04 11:44:09 :: found dns_domain in configuration None
2009/11/04 11:44:09 :: found passphrase in configuration 0ff1c361
2009/11/04 11:44:09 :: found gateway in configuration None
2009/11/04 11:44:09 :: found use_global_dns in configuration 0
2009/11/04 11:44:09 :: found disconnect in configuration None
2009/11/04 11:44:09 :: found ip in configuration None
2009/11/04 11:44:09 :: found beforescript in configuration None
2009/11/04 11:44:09 :: found psk in configuration 9c2f613156e3b74f164315e56d7e84e6e1858a893a052553b49549497a0df39b
2009/11/04 11:44:09 :: found netmask in configuration None
2009/11/04 11:44:09 :: found key in configuration 0ff1c361
2009/11/04 11:44:09 :: found predisconnectscript in configuration None
2009/11/04 11:44:09 :: found enctype in configuration wpa
2009/11/04 11:44:09 :: found dns3 in configuration None
2009/11/04 11:44:09 :: found dns2 in configuration None
2009/11/04 11:44:09 :: found dns1 in configuration None
2009/11/04 11:44:09 :: found use_settings_globally in configuration 0
2009/11/04 11:44:09 :: found use_static_dns in configuration 0
2009/11/04 11:44:09 :: found apsk in configuration db8280017d8480f21c233d11730b3bab67a4a073390740de2b51eb395b31cf2d
2009/11/04 11:44:09 :: found automatic in configuration True
2009/11/04 11:44:09 :: found search_domain in configuration None
2009/11/04 11:44:09 :: found afterscript in configuration None
2009/11/04 11:44:09 :: found postdisconnectscript in configuration None
2009/11/04 11:44:09 :: found dns_domain in configuration None
2009/11/04 11:44:09 :: found gateway in configuration None
2009/11/04 11:44:09 :: found use_global_dns in configuration 0
2009/11/04 11:44:09 :: found disconnect in configuration None
2009/11/04 11:44:09 :: found ip in configuration None
2009/11/04 11:44:09 :: found beforescript in configuration None
2009/11/04 11:44:09 :: found psk in configuration aea2389d8d9d253c179fec12b21e324bde2212d4d199a6bdd989ba4ba3715292
2009/11/04 11:44:09 :: found netmask in configuration None
2009/11/04 11:44:09 :: found key in configuration 0ff1c361
2009/11/04 11:44:09 :: found predisconnectscript in configuration None
2009/11/04 11:44:09 :: found enctype in configuration wpa
2009/11/04 11:44:09 :: found dns3 in configuration None
2009/11/04 11:44:09 :: found dns2 in configuration None
2009/11/04 11:44:09 :: found dns1 in configuration None
2009/11/04 11:44:09 :: found use_settings_globally in configuration 1
2009/11/04 11:44:09 :: found use_static_dns in configuration 0
2009/11/04 11:44:09 :: found apsk in configuration 0ff1c361
2009/11/04 11:44:09 :: found automatic in configuration False
2009/11/04 11:44:09 :: found search_domain in configuration None
2009/11/04 11:44:09 :: found afterscript in configuration None
2009/11/04 11:44:09 :: found postdisconnectscript in configuration None
2009/11/04 11:44:09 :: found dns_domain in configuration None
2009/11/04 11:44:09 :: found netmask in configuration None
2009/11/04 11:44:09 :: found key in configuration 0ff1C361
2009/11/04 11:44:09 :: found predisconnectscript in configuration None
2009/11/04 11:44:09 :: found gateway in configuration None
2009/11/04 11:44:09 :: found use_global_dns in configuration 0
2009/11/04 11:44:09 :: found dns3 in configuration None
2009/11/04 11:44:09 :: found dns2 in configuration None
2009/11/04 11:44:09 :: found search_domain in configuration None
2009/11/04 11:44:09 :: found use_settings_globally in configuration 0
2009/11/04 11:44:09 :: found use_static_dns in configuration 0
2009/11/04 11:44:09 :: found ip in configuration None
2009/11/04 11:44:09 :: found beforescript in configuration None
2009/11/04 11:44:09 :: found enctype in configuration wpa
2009/11/04 11:44:09 :: found dns1 in configuration None
2009/11/04 11:44:09 :: found afterscript in configuration None
2009/11/04 11:44:09 :: found ip in configuration None
2009/11/04 11:44:09 :: found netmask in configuration None
2009/11/04 11:44:09 :: found key in configuration 0ff1c361
2009/11/04 11:44:09 :: found gateway in configuration None
2009/11/04 11:44:09 :: found use_global_dns in configuration 0
2009/11/04 11:44:09 :: found disconnect in configuration None
2009/11/04 11:44:09 :: found dns3 in configuration None
2009/11/04 11:44:09 :: found dns1 in configuration None
2009/11/04 11:44:09 :: found use_settings_globally in configuration 0
2009/11/04 11:44:09 :: found use_static_dns in configuration 0
2009/11/04 11:44:09 :: found dns2 in configuration None
2009/11/04 11:44:09 :: found beforescript in configuration None
2009/11/04 11:44:09 :: found enctype in configuration wpa
2009/11/04 11:44:09 :: found automatic in configuration False
2009/11/04 11:44:09 :: <hidden> has profile
2009/11/04 11:44:09 :: trying to automatically connect to...<hidden>
2009/11/04 11:44:09 :: Connecting to wireless network <hidden>
2009/11/04 11:44:09 :: /sbin/dhclient -r eth0
2009/11/04 11:44:10 :: ifconfig eth0 0.0.0.0 
2009/11/04 11:44:10 :: /sbin/ip route flush dev eth0
2009/11/04 11:44:10 :: ifconfig eth0 down
2009/11/04 11:44:10 :: ifconfig eth0 up
2009/11/04 11:44:10 :: Putting interface down
2009/11/04 11:44:10 :: ifconfig wlan0 down
2009/11/04 11:44:10 :: Releasing DHCP leases...
2009/11/04 11:44:10 :: /sbin/dhclient -r wlan0
2009/11/04 11:44:11 :: Setting false IP...
2009/11/04 11:44:11 :: ifconfig wlan0 0.0.0.0 
2009/11/04 11:44:11 :: Stopping wpa_supplicant
2009/11/04 11:44:11 :: wpa_cli -i wlan0 terminate
2009/11/04 11:44:11 :: Flushing the routing table...
2009/11/04 11:44:11 :: /sbin/ip route flush dev wlan0
2009/11/04 11:44:11 :: iwconfig wlan0 mode managed
2009/11/04 11:44:11 :: Putting interface up...
2009/11/04 11:44:11 :: ifconfig wlan0 up
2009/11/04 11:44:11 :: enctype is wpa
2009/11/04 11:44:11 :: Generating psk...
2009/11/04 11:44:11 :: ['/usr/bin/wpa_passphrase', '<hidden>', '0ff1c361']
2009/11/04 11:44:11 :: Attempting to authenticate...
2009/11/04 11:44:11 :: ['wpa_supplicant', '-B', '-i', 'wlan0', '-c', '/var/lib/wicd/configurations/000ff771a090', '-D', 'wext']
2009/11/04 11:44:11 :: ['iwconfig', 'wlan0', 'essid', '<hidden>']
2009/11/04 11:44:11 :: iwconfig wlan0 channel 11
2009/11/04 11:44:11 :: iwconfig wlan0 ap 00:0F:F7:71:A0:90
2009/11/04 11:44:11 :: WPA_CLI RESULT IS DISCONNECTED
2009/11/04 11:44:12 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:13 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:14 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:15 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:16 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:17 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:18 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:19 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:20 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:21 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:22 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:23 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:24 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:25 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:26 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:27 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:28 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:29 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:30 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:31 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:32 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:33 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:34 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:35 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:36 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:37 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:38 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:39 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:40 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:41 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:42 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:43 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:44 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:45 :: WPA_CLI RESULT IS SCANNING
2009/11/04 11:44:46 :: wpa_supplicant authentication may have failed.
2009/11/04 11:44:46 :: Running DHCP
2009/11/04 11:44:46 :: /sbin/dhclient wlan0
2009/11/04 11:44:46 :: Internet Systems Consortium DHCP Client V3.1.2
2009/11/04 11:44:46 :: Copyright 2004-2008 Internet Systems Consortium.
2009/11/04 11:44:46 :: All rights reserved.
2009/11/04 11:44:46 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2009/11/04 11:44:46 :: 
2009/11/04 11:44:47 :: Listening on LPF/wlan0/00:1f:3b:5b:04:dd
2009/11/04 11:44:47 :: Sending on   LPF/wlan0/00:1f:3b:5b:04:dd
2009/11/04 11:44:47 :: Sending on   Socket/fallback
2009/11/04 11:44:49 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
2009/11/04 11:44:54 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
2009/11/04 11:45:00 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
2009/11/04 11:45:07 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
2009/11/04 11:45:14 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
2009/11/04 11:45:32 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
2009/11/04 11:45:44 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
2009/11/04 11:45:50 :: No DHCPOFFERS received.
2009/11/04 11:45:50 :: No working leases in persistent database - sleeping.
2009/11/04 11:45:59 :: DHCP connection failed
2009/11/04 11:45:59 :: exiting connection thread
2009/11/04 11:46:00 :: Sending connection attempt result dhcp_failed


Really need some help here. I don't think its wicd as my netbook still won't connect either. Only common factor here is the OS and AP

---

### Post by mab494 on 2009-11-04
No wireless for me since upgrade either.  Very frsutrating. Latitude D610

---

### Post by mab494 on 2009-11-04
If anyone has issues with the D610 and wireless from a 9.10 clean install - try;-
 
sudo apt-get install bcmwl-kernel-source
 
Then System --> Administration --> Hardware Drivers and install the broadcom driver that is there.  I now am connected to the internet wirelessly.

---


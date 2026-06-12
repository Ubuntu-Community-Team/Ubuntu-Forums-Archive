---
title: "Wireless can see every network except my own"
date: 2008-09-06
forum: General Help
---

### Post by dr_james2k on 2008-09-06
Hi, I seem to be having a rather odd problem.  I've been reading through the forums for some time trying to find a solution but so far I have found little similar to the problem I am having.  My wireless cannot see my own home network,  I'm not sure on what is causing this problem.  Its a WPA2 secure network.  I can see other networks in the area (other which are also WPA2) but not my own.  I've also had this problem where I work where the network I want to use is not visible to the network manager.  I currently used WICD but I have swapped back and forth between it and the default network manager and it is the same with both, I can see all networks except the one I want.  I'm currently curious if ubuntu (outside of WICD as I have cleared its config files a few times) stores information on past networks.  Any info would be greatley appreciated.  

Here's my WICD log file, see if anyone can spot anything wrong with it:
```
2008/09/06 14:04:06 :: ---------------------------
2008/09/06 14:04:06 :: wicd initalizing...
2008/09/06 14:04:06 :: ---------------------------
2008/09/06 14:04:06 :: found wireless interface in configuration... setting wireless interface wlan0
2008/09/06 14:04:06 :: found wired interface in configuration... setting wired interface eth0
2008/09/06 14:04:06 :: found wpa driver in configuration... setting wpa driver madwifi
2008/09/06 14:04:06 :: 0
2008/09/06 14:04:06 :: setting use global dns to 0
2008/09/06 14:04:06 :: setting use global dns to boolean False
2008/09/06 14:04:06 :: setting global dns
2008/09/06 14:04:06 :: global dns servers are None None None
2008/09/06 14:04:06 :: wired autoconnection method is 1
2008/09/06 14:04:06 :: wireless configuration file found...
2008/09/06 14:04:06 :: wired configuration file found...
2008/09/06 14:04:06 :: chmoding configuration files 0600...
2008/09/06 14:04:06 :: chowning configuration files root:root...
2008/09/06 14:04:06 :: autodetected wireless interface... automatically detected wireless interface wlan0
2008/09/06 14:04:06 :: wlan0
2008/09/06 14:04:06 :: using wireless interface... returning wireless interface to client
2008/09/06 14:04:06 :: wlan0
2008/09/06 14:04:06 :: autoconnecting... returning wireless interface to client
2008/09/06 14:04:06 :: wlan0
2008/09/06 14:04:06 :: scanning start
2008/09/06 14:04:06 ::  ##### 00:1B:2F:42:65:6A
2008/09/06 14:04:09 :: scanning done
2008/09/06 14:04:09 :: found 1 networks: 00:1B:2F:42:65:6A
2008/09/06 14:04:09 :: 
2008/09/06 14:04:09 :: ['UniWired', 'HomeWired']
2008/09/06 14:04:09 :: returned beforescript with value of None to client...
2008/09/06 14:04:09 :: returned afterscript with value of None to client...
2008/09/06 14:04:09 :: returned disconnectscript with value of None to client...
2008/09/06 14:04:09 :: interface down... eth0
2008/09/06 14:04:09 :: setting false ip... 0.0.0.0 on eth0
2008/09/06 14:04:09 :: interface up... eth0
2008/09/06 14:04:09 :: killing wpa_supplicant, dhclient, dhclient3
2008/09/06 14:04:09 :: flushing the routing table...
2008/09/06 14:04:09 :: running dhcp...
2008/09/06 14:04:10 :: Attempting to autoconnect with wired interface...
2008/09/06 14:04:10 :: wired connecting True
2008/09/06 14:04:10 :: wired connecting True
2008/09/06 14:04:11 :: Checking for static DNS...
2008/09/06 14:04:12 :: Use static DNS: False
2008/09/06 14:04:12 :: Use global DNS: False
2008/09/06 14:04:12 :: wired connecting False
2008/09/06 14:04:12 :: ...done autoconnecting.
2008/09/06 14:04:12 :: None
2008/09/06 14:04:12 :: returning wireless interface to client
2008/09/06 14:05:37 :: returning wireless interface to client
2008/09/06 14:05:37 :: returning wireless interface to client
2008/09/06 14:05:37 :: returning wireless interface to client
2008/09/06 14:05:37 :: returning wireless interface to client
2008/09/06 14:05:37 :: returning wireless interface to client
2008/09/06 14:05:37 :: returning wireless interface to client
2008/09/06 14:05:40 :: returning wireless interface to client
2008/09/06 14:05:40 :: returning wireless interface to client
2008/09/06 14:05:40 :: returning wireless interface to client
2008/09/06 14:05:40 :: returning wireless interface to client
2008/09/06 14:05:40 :: returning wireless interface to client
2008/09/06 14:05:40 :: returning wireless interface to client
2008/09/06 14:05:43 :: returning wireless interface to client
2008/09/06 14:05:43 :: returning wireless interface to client
2008/09/06 14:05:43 :: returning wireless interface to client
2008/09/06 14:05:43 :: returning wireless interface to client
2008/09/06 14:05:43 :: returning wireless interface to client
2008/09/06 14:05:43 :: returning wireless interface to client
2008/09/06 14:05:47 :: returning wireless interface to client
2008/09/06 14:05:47 :: returning wireless interface to client
2008/09/06 14:05:47 :: returning wireless interface to client
2008/09/06 14:05:47 :: returning wireless interface to client
2008/09/06 14:05:47 :: returning wireless interface to client
2008/09/06 14:05:47 :: returning wireless interface to client
2008/09/06 14:05:49 :: returning wireless interface to client
2008/09/06 14:05:49 :: returning wireless interface to client
2008/09/06 14:05:49 :: returning wireless interface to client
2008/09/06 14:05:49 :: returning wireless interface to client
2008/09/06 14:05:49 :: returning wireless interface to client
2008/09/06 14:05:49 :: returning wireless interface to client
2008/09/06 14:05:52 :: returning wireless interface to client
2008/09/06 14:05:52 :: returning wireless interface to client
2008/09/06 14:05:52 :: returning wireless interface to client
2008/09/06 14:05:52 :: returning wireless interface to client
2008/09/06 14:05:52 :: returning wireless interface to client
2008/09/06 14:05:52 :: returning wireless interface to client
2008/09/06 14:05:55 :: returning wireless interface to client
2008/09/06 14:05:55 :: returning wireless interface to client
2008/09/06 14:05:55 :: returning wireless interface to client
2008/09/06 14:05:55 :: returning wireless interface to client
2008/09/06 14:05:55 :: returning wireless interface to client
2008/09/06 14:05:55 :: returning wireless interface to client
2008/09/06 14:05:58 :: returning wireless interface to client
2008/09/06 14:05:58 :: returning wireless interface to client
2008/09/06 14:05:58 :: returning wireless interface to client
2008/09/06 14:05:58 :: returning wireless interface to client
2008/09/06 14:05:58 :: returning wireless interface to client
2008/09/06 14:05:58 :: returning wireless interface to client
2008/09/06 14:06:01 :: returning wireless interface to client
2008/09/06 14:06:01 :: returning wireless interface to client
2008/09/06 14:06:01 :: returning wireless interface to client
2008/09/06 14:06:01 :: returning wireless interface to client
2008/09/06 14:06:01 :: returning wireless interface to client
2008/09/06 14:06:01 :: returning wireless interface to client
2008/09/06 14:06:04 :: returning wireless interface to client
2008/09/06 14:06:04 :: returning wireless interface to client
2008/09/06 14:06:04 :: returning wireless interface to client
2008/09/06 14:06:04 :: returning wireless interface to client
2008/09/06 14:06:04 :: returning wireless interface to client
2008/09/06 14:06:04 :: returning wireless interface to client
2008/09/06 14:06:07 :: returning wireless interface to client
2008/09/06 14:06:07 :: returning wireless interface to client
2008/09/06 14:06:07 :: returning wireless interface to client
2008/09/06 14:06:07 :: returning wireless interface to client
2008/09/06 14:06:07 :: returning wireless interface to client
2008/09/06 14:06:07 :: returning wireless interface to client
2008/09/06 14:06:10 :: returning wireless interface to client
2008/09/06 14:06:10 :: returning wireless interface to client
2008/09/06 14:06:10 :: returning wireless interface to client
2008/09/06 14:06:10 :: returning wireless interface to client
2008/09/06 14:06:10 :: returning wireless interface to client
2008/09/06 14:06:10 :: ['UniWired', 'HomeWired']
2008/09/06 14:06:12 :: ['UniWired', 'HomeWired']
2008/09/06 14:06:12 :: returned default with value of True to client...
2008/09/06 14:06:12 :: returned ip with value of None to client...
2008/09/06 14:06:12 :: returned netmask with value of None to client...
2008/09/06 14:06:12 :: returned gateway with value of None to client...
2008/09/06 14:06:12 :: returned dns1 with value of None to client...
2008/09/06 14:06:12 :: returned dns2 with value of None to client...
2008/09/06 14:06:12 :: returned dns3 with value of None to client...
2008/09/06 14:06:12 :: returned beforescript with value of None to client...
2008/09/06 14:06:12 :: returned afterscript with value of None to client...
2008/09/06 14:06:12 :: returned disconnectscript with value of None to client...
2008/09/06 14:06:12 :: returned default with value of False to client...
2008/09/06 14:06:12 :: set default to False
2008/09/06 14:06:12 :: setting profile for UniWired
2008/09/06 14:06:12 :: returned ip with value of None to client...
2008/09/06 14:06:12 :: returned netmask with value of None to client...
2008/09/06 14:06:12 :: returned gateway with value of None to client...
2008/09/06 14:06:12 :: returned dns1 with value of None to client...
2008/09/06 14:06:12 :: returned dns2 with value of None to client...
2008/09/06 14:06:12 :: returned dns3 with value of None to client...
2008/09/06 14:06:12 :: returned beforescript with value of None to client...
2008/09/06 14:06:12 :: returned afterscript with value of None to client...
2008/09/06 14:06:12 :: returned disconnectscript with value of None to client...
2008/09/06 14:06:12 :: returned default with value of True to client...
2008/09/06 14:06:12 :: profileList =  ['HomeWired', 'UniWired']
2008/09/06 14:06:12 :: profile =  HomeWired
2008/09/06 14:06:12 :: removing existing default
2008/09/06 14:06:12 :: setting profile for HomeWired
2008/09/06 14:06:12 :: profile =  UniWired
2008/09/06 14:06:12 :: set default to True
2008/09/06 14:06:12 :: setting profile for HomeWired
2008/09/06 14:06:12 :: ['HomeWired', 'UniWired']
2008/09/06 14:06:12 :: returned number of networks... 1
2008/09/06 14:06:12 :: returned number of networks... 1
2008/09/06 14:06:12 :: returned number of networks... 1
2008/09/06 14:06:12 :: returned wireless network 0 property essid of type <type 'str'>
2008/09/06 14:06:12 :: returned wireless network 0 property essid of type <type 'str'>
2008/09/06 14:06:12 :: returned wireless network 0 property essid of type <type 'str'>
2008/09/06 14:06:12 :: returned wireless network 0 property ip of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property netmask of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property gateway of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property use_global_dns of type <type 'bool'>
2008/09/06 14:06:12 :: returned wireless network 0 property dns1 of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property dns2 of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property dns3 of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property beforescript of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property afterscript of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property disconnectscript of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property automatic of type <type 'bool'>
2008/09/06 14:06:12 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property key of type <type 'NoneType'>
2008/09/06 14:06:12 :: returned wireless network 0 property quality of type <type 'int'>
2008/09/06 14:06:12 :: returned wireless network 0 property strength of type <type 'str'>
2008/09/06 14:06:12 :: returned wpa driver
2008/09/06 14:06:12 :: returned wpa driver
2008/09/06 14:06:12 :: returned wireless network 0 property bssid of type <type 'str'>
2008/09/06 14:06:12 :: returned wireless network 0 property mode of type <type 'str'>
2008/09/06 14:06:12 :: returned wireless network 0 property channel of type <type 'str'>
2008/09/06 14:06:12 :: returned wireless network 0 property encryption of type <type 'bool'>
2008/09/06 14:06:12 :: returned wireless network 0 property encryption_method of type <type 'str'>
2008/09/06 14:06:12 :: returning wireless interface to client
2008/09/06 14:06:13 :: returning wireless interface to client
2008/09/06 14:06:13 :: returning wireless interface to client
2008/09/06 14:06:13 :: returning wireless interface to client
2008/09/06 14:06:13 :: returning wireless interface to client
2008/09/06 14:06:13 :: returning wireless interface to client
2008/09/06 14:06:13 :: ['HomeWired', 'UniWired']
2008/09/06 14:06:14 :: ['HomeWired', 'UniWired']
2008/09/06 14:06:14 :: returned default with value of True to client...
2008/09/06 14:06:14 :: returned ip with value of None to client...
2008/09/06 14:06:14 :: returned netmask with value of None to client...
2008/09/06 14:06:14 :: returned gateway with value of None to client...
2008/09/06 14:06:14 :: returned dns1 with value of None to client...
2008/09/06 14:06:14 :: returned dns2 with value of None to client...
2008/09/06 14:06:14 :: returned dns3 with value of None to client...
2008/09/06 14:06:14 :: returned beforescript with value of None to client...
2008/09/06 14:06:14 :: returned afterscript with value of None to client...
2008/09/06 14:06:14 :: returned disconnectscript with value of None to client...
2008/09/06 14:06:14 :: returned default with value of True to client...
2008/09/06 14:06:14 :: ['HomeWired', 'UniWired']
2008/09/06 14:06:14 :: setting hidden essid: None
2008/09/06 14:06:14 :: scanning start
2008/09/06 14:06:14 ::  ##### 00:1B:2F:42:65:6A
2008/09/06 14:06:17 :: scanning done
2008/09/06 14:06:17 :: found 1 networks: 00:1B:2F:42:65:6A
2008/09/06 14:06:17 :: 
2008/09/06 14:06:17 :: returning wireless interface to client
2008/09/06 14:06:17 :: returning wireless interface to client
2008/09/06 14:06:17 :: returned number of networks... 1
2008/09/06 14:06:17 :: returning wireless interface to client
2008/09/06 14:06:17 :: returned number of networks... 1
2008/09/06 14:06:17 :: returning wireless interface to client
2008/09/06 14:06:17 :: returned number of networks... 1
2008/09/06 14:06:17 :: returning wireless interface to client
2008/09/06 14:06:17 :: returning wireless interface to client
2008/09/06 14:06:17 :: returned wireless network 0 property ip of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property netmask of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property gateway of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property use_global_dns of type <type 'bool'>
2008/09/06 14:06:18 :: returned wireless network 0 property dns1 of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property dns2 of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property dns3 of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property beforescript of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property afterscript of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property disconnectscript of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property automatic of type <type 'bool'>
2008/09/06 14:06:18 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property enctype of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property key of type <type 'NoneType'>
2008/09/06 14:06:18 :: returned wireless network 0 property quality of type <type 'int'>
2008/09/06 14:06:18 :: returned wireless network 0 property strength of type <type 'str'>
2008/09/06 14:06:18 :: returned wpa driver
2008/09/06 14:06:18 :: returned wpa driver
2008/09/06 14:06:18 :: returned wireless network 0 property bssid of type <type 'str'>
2008/09/06 14:06:18 :: returned wireless network 0 property mode of type <type 'str'>
2008/09/06 14:06:18 :: returned wireless network 0 property channel of type <type 'str'>
2008/09/06 14:06:18 :: returned wireless network 0 property encryption of type <type 'bool'>
2008/09/06 14:06:18 :: returned wireless network 0 property encryption_method of type <type 'str'>
2008/09/06 14:06:18 :: returning wireless interface to client
2008/09/06 14:06:19 :: returning wireless interface to client
2008/09/06 14:06:19 :: returning wireless interface to client
2008/09/06 14:06:19 :: returning wireless interface to client
2008/09/06 14:06:19 :: returning wireless interface to client
2008/09/06 14:06:19 :: returning wireless interface to client
2008/09/06 14:06:19 :: returning wireless interface to client
2008/09/06 14:06:22 :: returning wireless interface to client
2008/09/06 14:06:22 :: returning wireless interface to client
2008/09/06 14:06:22 :: returning wireless interface to client
2008/09/06 14:06:22 :: returning wireless interface to client
2008/09/06 14:06:22 :: returning wireless interface to client
2008/09/06 14:06:22 :: returning wireless interface to client
2008/09/06 14:06:25 :: returning wireless interface to client
2008/09/06 14:06:25 :: returning wireless interface to client
2008/09/06 14:06:25 :: returning wireless interface to client
2008/09/06 14:06:25 :: returning wireless interface to client
2008/09/06 14:06:25 :: returning wireless interface to client
2008/09/06 14:06:25 :: returning wireless interface to client
2008/09/06 14:06:28 :: returning wireless interface to client
2008/09/06 14:06:28 :: returning wireless interface to client
2008/09/06 14:06:28 :: returning wireless interface to client
2008/09/06 14:06:28 :: returning wireless interface to client
2008/09/06 14:06:28 :: returning wireless interface to client
2008/09/06 14:06:28 :: returning wireless interface to client
2008/09/06 14:06:34 :: returning wireless interface to client
2008/09/06 14:06:34 :: returning wireless interface to client
2008/09/06 14:06:34 :: returning wireless interface to client
2008/09/06 14:06:34 :: returning wireless interface to client
2008/09/06 14:06:34 :: returning wireless interface to client
2008/09/06 14:06:34 :: wired connecting False
2008/09/06 14:06:34 :: wireless connecting False
2008/09/06 14:06:34 :: returning wired ip 192.168.1.5
2008/09/06 14:06:34 :: returning wireless interface to client
2008/09/06 14:06:37 :: returning wireless interface to client
2008/09/06 14:06:37 :: returning wireless interface to client
2008/09/06 14:06:37 :: returning wireless interface to client
2008/09/06 14:06:37 :: returning wireless interface to client
2008/09/06 14:06:37 :: returning wireless interface to client
2008/09/06 14:06:37 :: returning wireless interface to client
2008/09/06 14:06:40 :: returning wireless interface to client
2008/09/06 14:06:40 :: returning wireless interface to client
2008/09/06 14:06:40 :: returning wireless interface to client
2008/09/06 14:06:40 :: returning wireless interface to client
2008/09/06 14:06:40 :: returning wireless interface to client
2008/09/06 14:06:40 :: returning wireless interface to client
2008/09/06 14:06:43 :: returning wireless interface to client
2008/09/06 14:06:43 :: returning wireless interface to client
2008/09/06 14:06:43 :: returning wireless interface to client
2008/09/06 14:06:43 :: returning wireless interface to client
2008/09/06 14:06:43 :: returning wireless interface to client
2008/09/06 14:06:43 :: returning wireless interface to client
2008/09/06 14:06:46 :: returning wireless interface to client
2008/09/06 14:06:46 :: returning wireless interface to client
2008/09/06 14:06:46 :: returning wireless interface to client
2008/09/06 14:06:46 :: returning wireless interface to client
2008/09/06 14:06:46 :: returning wireless interface to client
2008/09/06 14:06:46 :: returning wireless interface to client
2008/09/06 14:06:49 :: returning wireless interface to client
2008/09/06 14:06:49 :: returning wireless interface to client
2008/09/06 14:06:49 :: returning wireless interface to client
2008/09/06 14:06:49 :: returning wireless interface to client
2008/09/06 14:06:49 :: returning wireless interface to client
2008/09/06 14:06:49 :: returning wireless interface to client
2008/09/06 14:06:52 :: returning wireless interface to client
2008/09/06 14:06:52 :: returning wireless interface to client
2008/09/06 14:06:52 :: returning wireless interface to client
2008/09/06 14:06:52 :: returning wireless interface to client
2008/09/06 14:06:52 :: returning wireless interface to client
2008/09/06 14:06:52 :: returning wireless interface to client
2008/09/06 14:06:55 :: returning wireless interface to client
2008/09/06 14:06:55 :: returning wireless interface to client
2008/09/06 14:06:55 :: returning wireless interface to client
2008/09/06 14:06:55 :: returning wireless interface to client
2008/09/06 14:06:55 :: returning wireless interface to client
2008/09/06 14:06:55 :: returning wireless interface to client
2008/09/06 14:06:58 :: returning wireless interface to client
2008/09/06 14:06:58 :: returning wireless interface to client
2008/09/06 14:06:58 :: returning wireless interface to client
2008/09/06 14:06:58 :: returning wireless interface to client
2008/09/06 14:06:58 :: returning wireless interface to client
2008/09/06 14:06:58 :: returning wireless interface to client
2008/09/06 14:07:01 :: returning wireless interface to client
2008/09/06 14:07:01 :: returning wireless interface to client
2008/09/06 14:07:01 :: returning wireless interface to client
2008/09/06 14:07:01 :: returning wireless interface to client
2008/09/06 14:07:01 :: returning wireless interface to client
2008/09/06 14:07:01 :: returning wireless interface to client
2008/09/06 14:07:04 :: returning wireless interface to client
2008/09/06 14:07:04 :: returning wireless interface to client
2008/09/06 14:07:04 :: returning wireless interface to client
2008/09/06 14:07:04 :: returning wireless interface to client
2008/09/06 14:07:04 :: returning wireless interface to client
2008/09/06 14:07:04 :: returning wireless interface to client
2008/09/06 14:07:07 :: returning wireless interface to client
2008/09/06 14:07:07 :: returning wireless interface to client
2008/09/06 14:07:07 :: returning wireless interface to client
2008/09/06 14:07:07 :: returning wireless interface to client
2008/09/06 14:07:07 :: returning wireless interface to client
2008/09/06 14:07:07 :: returning wireless interface to client
2008/09/06 14:07:10 :: returning wireless interface to client
2008/09/06 14:07:10 :: returning wireless interface to client
2008/09/06 14:07:10 :: returning wireless interface to client
2008/09/06 14:07:10 :: returning wireless interface to client
2008/09/06 14:07:10 :: returning wireless interface to client
2008/09/06 14:07:10 :: returning wireless interface to client
2008/09/06 14:07:13 :: returning wireless interface to client
2008/09/06 14:07:13 :: returning wireless interface to client
2008/09/06 14:07:13 :: returning wireless interface to client
2008/09/06 14:07:13 :: returning wireless interface to client
2008/09/06 14:07:13 :: returning wireless interface to client
2008/09/06 14:07:13 :: returning wireless interface to client
2008/09/06 14:07:16 :: returning wireless interface to client
2008/09/06 14:07:16 :: returning wireless interface to client
2008/09/06 14:07:16 :: returning wireless interface to client
2008/09/06 14:07:16 :: returning wireless interface to client
2008/09/06 14:07:16 :: returning wireless interface to client
2008/09/06 14:07:16 :: 
```

---

### Post by Karpah on 2008-09-06
I'm not too familiar with how these things work, and this might be a silly question, but... is your wireless network set to broadcast its SSID?

My wireless right now can detect my next door neighbour's wireless, but not my own, because my SSID is set to private, not broadcast. However, if I manually type my network name, type and password into the Network screen, I can connect just fine.

---

### Post by sicofante on 2008-09-06
I experience the same problem every now and then. My workaround is to left-click on the Network Manager icon in the taskbar and select "Connect to other wireless network" (I'm translating from the Spanish interface, the orignal English menu may vary), then type the name of my own network. After I do so, I usually get it back on the list. after a few seconds.

Ubuntu does store the passwords of past networks. You can check the list by right-clicking on the same icon in the system tray and select "Edit wireless networks".

---

### Post by dr_james2k on 2008-09-06
Yeah, it does broadcast its SSID.  I'm currently on my desktop which can see the network even when its not connected to it.  Thanks for the prompt response though.

---

